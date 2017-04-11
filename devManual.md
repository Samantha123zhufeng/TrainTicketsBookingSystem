# �����ֲ�

## ��ع淶

1. �ļ�����������ͬ��淶��ͬ
2. �淶������: 
	1. ������ȫ��д�����������С�շ�������(Сд��ͷ)
	2. ��Ԫ���������ӿո�
	3. �������뺯��ͷͬ��
3. ʹ��sjtu���ֿռ�
4. ʹ��ͷ�ļ���������

*myClass.hpp*
```cpp
#ifndef SJTU_MYCLASS_HPP
#define SJTU_MYCLASS_HPP
namespace sjtu {

class myClass {
private:
public:
};

}
#endif
```

## ˼·ͼ��
�д�����!

## �ļ�����
| file name | description |
|:---:|:----:|
| system.hpp | ��Ʊϵͳ |
| train.hpp | ���� |
| plan.hpp | ���мƻ� |
| station.hpp | ��վ |
| ticket.hpp | ��Ʊ |
| user.hpp | ����Ա���û� |
| vector.hpp | vector���� |
| map.hpp | map���� |
| list.hpp | list���� |
| timer.hpp | ʱ�� |
| log.hpp | ϵͳ��־ |

## ��ӿ�

### ��8��

ע��: 
1. ��*�ű�ʾ�ݻ�ʵ��
2. ����Ҫ���õ��Ѿ�ʵ�ֺõĹ�����(��timer)����dev-tools����

#### station
��վ��, train��һ��"��Ƕ��", ĳ�����峵������·���е�ĳ����վ
��A���г������䲻ͬB���г����ᾭ�����Ϻ�վ, ��������Ϊ�ǲ�ͬ��

| return type | method | description |
|:----------:|:---------------:|:----------:|
| / | station(const string &_name, int _id, const string &_train, const timer &_stopTime, const timer &_departTIme, int _length, int _price[]) |  ���캯�� |
| string | getName() | ���ظó�վ������ |
| int | getId() | ���ظó�վ�ı�� |
| string | getTrain() | ���������ĳ��� |
| timer | getStopTime() | �����ڸó��δӳ�����ͣ���ڸ�վ��ʱ��� |
| timer | getDepartTime() | ���ظó��δӳ������뿪��վ��ʱ��� |
| int | getLength() | ���ظó��δӳ�����ͣ���ڸ�վ����ʻ����� |
| int | getPrice(int type) | ���ظó��ε�type������λ�ӳ�������վ��Ʊ�� ����type=1,2,3�ֱ��ʾһ����,������,������ |

#### plan
���мƻ���, train��һ��"��Ƕ��", ������������ʼ��ʱ��Ψһȷ��

| return type | method | description |
|:-----:|:------:|
| / | plan(const string &_train, const timer &_startTime, bool _status = false) | ���캯�� |
| string | getTrain() | ���������ĳ��� |
| timer | getStartTime() | ����ʼ��ʱ�� |
| bool | getStatus() | ���ط���״̬ |
| int | getLeftTickets(int type, int u, int v) | ���شӸó���uthվ�㵽vthվ��type������λʣ��Ʊ�� ����������벻�Ϸ��򷵻�0 |
| void | modifyStartTime() | �޸�ʼ��ʱ�� |
| void | modifyStatus(bool newStatus) | �޸���Ʊ״̬ |
| void | query(int type, int u, int v) | ���ʼ��ʱ��, ����״̬, ʣ��Ʊ�� |
| ticket | **orderTicket**(int type, int u, int v) | ���ض��õ�Ʊ |
| void | **disorderTicket**(const ticket &tk) | �˶���Ʊ |

ע��:
1. �����޸ľ���Ҫcheck����״̬Ϊfalse
2. ��Ʊ��ǵ��޸���Ʊ��Ϣ
3. ��Ʊ��Ϣ���޸����ѯҪ������״����ʵ��

#### ticket
��Ʊ��, ��¼һ�ų�Ʊ�������Ϣ

| return type | method | description |
|:-----:|:------:|
| / | ticket(const string &_train, const timer &_sartTime, int type, int u, int v | ���캯�� ����u/vΪ��/�յ�վ�ڸó����е�λ�� |
| string | getTrain() | ������������ |
| timer | getStartTime() | �����������мƻ���ʼ��ʱ�� |
| int | getType() | ������λ���� |
| int | getPrice() | ����Ʊ�� |
| friend std::ostream &  | operator<< (const std::ostream &os, const &obj) | �����������, ʼ��ʱ��, ��Ϊ����, Ʊ��, ���վ���յ�վ(, �����û���Ϣ) |
| user | **getUser**() | ���������û� |


### ��7��

#### timer

ʱ����, ���ڴ���ʱ����ص�����

| return type | method | description |
|:-----:|:------:|
| / | timer(int _yy = 0, int _mm = 0, int _dd = 0, int _hh = 0, int _ss = 0) | ���캯�� ����ss��ʾ�� |
| friend std::ostream & | operator<< (std::ostream &os, const timer &obj) | �� yy/mm/dd hh:ss �ĸ�ʽ���ʱ����Ϣ |
| friend timer | operator- (const timer &obj1, const timer &obj2) | ���obj1��obj2��ʱ��� Ҫ��obj2>obj1�����׳�exception()�쳣 Ҫ�����뾡���Ϸ����ֻ������������� |
| friend bool | operator == (const timer &obj1, const timer &obj2) | �ȽϺ��� |
| friend bool | operator < (const timer &obj1, const timer &obj2) | �ȽϺ��� |
| friend bool | operator > (const timer &obj1, const timer &obj2) | �ȽϺ��� |
| friend bool | operator <= (const timer &obj1, const timer &obj2)  | �ȽϺ��� |
| friend bool | operator >= (const timer &obj1, const timer &obj2) | �ȽϺ��� |

