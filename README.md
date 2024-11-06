<p align="center">
    <a href="https://www.python.org/psf-landing/" target="_blank">
        <img src="https://www.python.org/static/community_logos/python-logo.png" height="60px">
    </a>
    <h1 align="center">Python Stress Tool</h1>
    <br>
</p>

Stress test tool with statistical TPS reports based on Worker Dispatcher in Python

[![PyPI](https://img.shields.io/pypi/v/worker-dispatcher)](https://pypi.org/project/stress-tool/)
![](https://img.shields.io/pypi/implementation/stress-tool)



Features
--------

- Based on ***Worker Dispatcher** to managed workers*

- ***Statistical TPS Report** in Excel sheets*

- ***Customized Config** for the report*  


---

OUTLINE
-------

- [Demonstration](#demonstration)
- [Introduction](#introduction)
- [Installation](#installation)

---

DEMONSTRATION
-------------

Just write your own callback functions based on the [Worker Dispatcher](https://github.com/yidas/python-worker-dispatcher) library, then run it and generate the report file:

```bash
import stress_test

def each_task(id: int, config, task, log):
    response = requests.get(config['my_endpoint'] + task)
    return response

def main():

    results = stress_test.start({
        'task': {
            'list': ['ORD_AH001', 'ORD_KL502', '...' , 'ORD_GR393'],
            'callback': each_task,
            'config': {
                'my_endpoint': 'https://your.name/order-handler/'
            },
        }
    })

    if results != False:

        file_path = stress_test.generate_report(file_path='./tps-report.xlsx')
        print("Report has been successfully generated at {}".format(file_path))

if __name__ == '__main__':
    main()
```

<img src="https://github.com/yidas/python-stress-tool/blob/main/img/demonstration_excel.png?raw=true" width="400px" />

---

INTRODUCTION
------------




---

INSTALLATION
------------
