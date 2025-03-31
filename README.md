<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
</head>
<body>
  <h1>🛠️ Entorno de Desarrollo con Vagrant + Ansible</h1>

  <p>Este repositorio crea dos máquinas virtuales usando Vagrant y VirtualBox. Ambas VMs están aprovisionadas con Ansible (usando <code>ansible_local</code>) para instalar y configurar automáticamente:</p>

  <ul>
    <li>Una VM con <strong>Docker</strong></li>
    <li>Una VM con <strong>Nginx</strong> sirviendo una página web</li>
  </ul>

  <h2>📦 Requisitos</h2>
  <p>Asegúrate de tener instaladas las siguientes herramientas:</p>
  <ul>
    <li><a href="https://www.virtualbox.org/">VirtualBox</a></li>
    <li><a href="https://www.vagrantup.com/">Vagrant</a></li>
  </ul>

  <h2>🚀 Instalación y uso</h2>
  <ol>
    <li><strong>Clona este repositorio:</strong>
      <pre><code>git clone https://github.com/tu_usuario/tu_repositorio.git
cd tu_repositorio</code></pre>
    </li>
    <li><strong>Inicia las máquinas virtuales:</strong>
      <pre><code>vagrant up</code></pre>
    </li>
  </ol>

  <p>Esto hará lo siguiente:</p>
  <ul>
    <li>Descargará la imagen base <code>generic/ubuntu2004</code> si no la tienes.</li>
    <li>Creará dos VMs: <code>docker_vm</code> y <code>web_vm</code>.</li>
    <li>Usará Ansible Local para configurar cada una.</li>
  </ul>

  <h2>🌐 Acceso a los servicios</h2>
  <table border="1" cellpadding="5" cellspacing="0">
    <thead>
      <tr>
        <th>Servicio</th>
        <th>VM</th>
        <th>Puerto Host</th>
        <th>Puerto Guest</th>
        <th>URL</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Docker</td>
        <td>docker_vm</td>
        <td>9091</td>
        <td>3031</td>
        <td><a href="http://localhost:9091">http://localhost:9091</a></td>
      </tr>
      <tr>
        <td>Nginx</td>
        <td>web_vm</td>
        <td>8080</td>
        <td>80</td>
        <td><a href="http://localhost:8080">http://localhost:8080</a></td>
      </tr>
    </tbody>
  </table>

  <h2>📁 Estructura</h2>
  <pre><code>├── Vagrantfile
├── playbook.yaml         # Configura Docker en docker_vm
└── playbook_web.yaml     # Configura Nginx en web_vm</code></pre>

  <h2>🔧 Comandos útiles</h2>
  <ul>
    <li><strong>Recrear las máquinas desde cero:</strong>
      <pre><code>vagrant destroy -f && vagrant up</code></pre>
    </li>
    <li><strong>Conectarse a una VM:</strong>
      <pre><code>vagrant ssh docker_vm
vagrant ssh web_vm</code></pre>
    </li>
    <li><strong>Detener las VMs:</strong>
      <pre><code>vagrant halt</code></pre>
    </li>
  </ul>

  <h2>🧽 Limpieza</h2>
  <p>Para eliminar completamente las VMs y el entorno:</p>
  <pre><code>vagrant destroy</code></pre>

  <h2>✅ Notas</h2>
  <ul>
    <li>Ambas VMs usan <code>ansible_local</code>, por lo que Ansible se instala dentro de cada VM y se ejecuta desde allí.</li>
    <li>Los roles están definidos directamente en los playbooks (<code>playbook.yaml</code> y <code>playbook_web.yaml</code>).</li>
    <li>Puedes modificar los playbooks para adaptar la configuración a tus necesidades.</li>
  </ul>
</body>
</html>
