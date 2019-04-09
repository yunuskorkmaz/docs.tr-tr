---
title: 'Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: cb1cb03a078eeb273c69cc3c49b3ef2173c0a49c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084941"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma
Svcutil.exe gibi meta veri hizmetleri, sözleşmeler ve derlenmiş derlemelerde veri türlerini dışarı aktarabilirsiniz:  
  
-   Tüm meta verilerini aktarmak için Svcutil.exe, kullanarak bir derleme kümesi için hizmet sözleşmelerini derlenmiş girdi parametresi olarak derlemelerini belirtin. Bu varsayılan davranıştır.  
  
-   Svcutil.exe kullanılarak derlenmiş bir hizmet için meta verileri dışarı aktarmak için hizmet derleme veya derlemeler giriş parametrelerini belirtin. Kullanmalısınız `/serviceName` vermek istediğiniz hizmetin yapılandırma adını belirtmek için seçeneği. Svcutil.exe yapılandırma dosyası için belirtilen çalıştırılabilir derlemesinin otomatik olarak yükler.  
  
-   Bir derleme kümesi içindeki tüm veri anlaşması türleri dışarı aktarmak için kullanın `/dataContractOnly` seçeneği.  
  
> [!NOTE]
>  Kullanım `/reference` herhangi bir bağımlı derleme için dosya yollarını belirtmek için seçeneği.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Meta verileri derlenmiş Hizmet sözleşmeleri ile dışarı aktarmak için  
  
1.  Bir veya daha fazla sınıf libraries.1 içine, hizmet sözleşmesi uygulamaları derleme  
  
2.  Svcutil.exe derlenmiş derlemeleri üzerinde çalıştırın.  
  
    > [!NOTE]
    >  Kullanmanız gerekebilir `/reference` geçme herhangi bir bağımlı derleme için dosya yolunu belirtin.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Derlenmiş bir hizmet için meta verileri dışarı aktarmak için  
  
1.  Yürütülebilir bir derleme halinde hizmet uygulamanızı derleyin.  
  
2.  Hizmeti yürütülebilir dosyası için bir yapılandırma dosyası oluşturun ve bir hizmet yapılandırması ekleyin.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3.  Svcutil.exe derlenmiş hizmet yürütülebilir kullanarak çalıştırın `/serviceName` hizmetin yapılandırma adını belirtmek için anahtar.  
  
    > [!NOTE]
    >  Kullanmanız gerekebilir `/reference` geçme herhangi bir bağımlı derleme için dosya yolunu belirtin.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Derlenmiş veri anlaşmaları için meta verileri dışarı aktarmak için  
  
1.  İçine bir veya daha fazla sınıf kitaplıkları, veri sözleşme uygulamaları derleyin.  
  
2.  Kullanılarak derlenen derlemeler svcutil.exe çalıştırmak `/dataContract` yalnızca meta verilerin veri sözleşmeleri oluşturulması belirtmek için anahtar.  
  
    > [!NOTE]
    >  Kullanmanız gerekebilir `/reference` geçme herhangi bir bağımlı derleme için dosya yolunu belirtin.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir Basit Hizmet uygulaması ve yapılandırması için meta verileri oluşturmak gösterilmiştir.  
  
 Hizmet sözleşmesi için meta verileri dışarı aktarmak için.  
  
```  
svcutil.exe Contracts.dll  
```  
  
 Veri sözleşmeleri için meta verileri dışarı aktarmak için.  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Hizmet uygulaması için meta verileri dışarı aktarmak için.  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 `<path>` Contracts.dll yoludur.  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
