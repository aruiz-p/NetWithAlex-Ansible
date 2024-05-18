## Ansible Study Notes

This is complementary material for the study notes created in this <a href="www.netwhithalex.blog"> post </a>

### Built With

* [![Ansible][Ansible.io]][Ansible-url]
* [![Jinja][Jinja.io]][Jinja-url]

### Prerequisites

It is recommended to have a virtualized environment to emulate network devices and ansible server node.  

I used [GNS3](https://www.gns3.com/) running on my local machine

From the marketplace you can look for the following appliances and import them to your GNS3 server:
* Cisco IOU L3
* Cisco IOU L2
* Network Automation

### Topology

<img src="images/Ans-topo.png" alt="Topology" width="400" height="300">

### Getting started

#### 1. Configure devices and enable SSH access required for Ansible. 
   Inside the _additional materials_ folder you can find the initial running config of the network devices, change it accordingly. You might still need to    generate the ssh key manually with 
   ```sh
   crypto key generate rsa modulus 2048
   ```
   If you shut down the IOU devices, the crypto keys will be erased, you can run the  _generate_ssh_key.yml_  to create it on all devices 
   ```sh
   ansible-playbook generate_ssh_key.yml -i inventory_insecure
   ```
   At any time you can use the _erase_config.yml_ to erase configuration before pushing it again with through a playbook. 

#### 2. Explore _ansible_1_
   * This folder contains a playbook to configure Loopbacks and OSPF process. Notice tasks are repeated multiple times
   * The inventory file contains user and password information
   * The ansible.cfg file is using default information. To run the playbook you need to specify the inventory file (_-i option_).
   ```sh 
   ansible-playbook manual_configuration.yml -i inventory_insecure
   ```
  
#### 3. Explore _ansible_2_
   * This folder contains a playbook to configure Loopbacks and OSPF process using variables. This 2 tasks are enough to configure the 4 devices. 
   * The inventory file is not containing user and password information. Instead, this information is passed on the playbook itself.  
   * The ansible.cfg file was slightly altered to point to the local inventory file. Playbook can be run without _-i option_. 
   ```sh
   ansible-playbook variables_configuration.yml
   ```

#### 4. Explore _ansible_3_
   ```js
   const API_KEY = 'ENTER YOUR API';
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3
    - [ ] Nested Feature

See the [open issues](https://github.com/aruiz-p/repo_name/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Your Name - [linkedin-shield](https://twitter.com/twitter_handle) - netwithalex@gmail.com


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[Ansible.io]: https://img.shields.io/badge/Ansible-000000?style=for-the-badge&logo=ansible
[Ansible-url]: https://www.ansible.com/
[Jinja.io]: https://img.shields.io/badge/Jinja-B41717?style=for-the-badge&logo=jinja
[Jinja-url]: https://jinja.palletsprojects.com/en/3.1.x/templates/
[license-shield]: https://img.shields.io/github/license/aruiz-p/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/aruiz-p/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png

