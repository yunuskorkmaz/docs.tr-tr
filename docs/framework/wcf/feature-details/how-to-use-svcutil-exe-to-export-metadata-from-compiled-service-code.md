---
title: 'Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: b8ddbaf896ee4c6ea8b6f8e8ce7d0ecef28140ea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932568"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma
Svcutil. exe, derlenmiş derlemelerde hizmetler, sözleşmeler ve veri türleri için meta verileri aşağıdaki gibi dışarı aktarabilir:  
  
- Svcutil. exe ' yi kullanarak bir derleme kümesine yönelik tüm derlenmiş hizmet sözleşmeleri için meta verileri dışarı aktarmak için, derlemeleri giriş parametreleri olarak belirtin. Bu varsayılan davranıştır.  
  
- Svcutil. exe ' yi kullanarak derlenmiş bir hizmetin meta verilerini dışa aktarmak için, hizmet derlemesini veya derlemeleri giriş parametreleri olarak belirtin. Dışarı aktarmak istediğiniz hizmetin `/serviceName` yapılandırma adını belirtmek için seçeneğini kullanmanız gerekir. Svcutil. exe, belirtilen yürütülebilir derleme için yapılandırma dosyasını otomatik olarak yükler.  
  
- Bir derleme kümesi içindeki tüm veri anlaşması türlerini dışarı aktarmak için `/dataContractOnly` seçeneğini kullanın.  
  
> [!NOTE]
> Herhangi bir bağımlı derlemeye dosya yollarını belirtmek için seçeneğinikullanın.`/reference`  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Derlenmiş hizmet sözleşmeleri için meta verileri dışarı aktarmak için  
  
1. Hizmet sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin. 1  
  
2. Derlenen derlemelerde Svcutil. exe ' yi çalıştırın.  
  
    > [!NOTE]
    > Herhangi bir bağımlı derlemeye dosya yolunu `/reference` belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Derlenmiş bir hizmetin meta verilerini dışarı aktarmak için  
  
1. Hizmet uygulamanızı yürütülebilir bir derlemede derleyin.  
  
2. Hizmet yürütülebilir dosyanız için bir yapılandırma dosyası oluşturun ve bir hizmet yapılandırması ekleyin.  
  
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
  
3. Hizmetin yapılandırma adını belirtmek için `/serviceName` anahtarı kullanarak derlenmiş hizmet yürütülebilir dosyası üzerinde Svcutil. exe ' yi çalıştırın.  
  
    > [!NOTE]
    > Herhangi bir bağımlı derlemeye dosya yolunu `/reference` belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Derlenen veri sözleşmeleri için meta verileri dışarı aktarmak için  
  
1. Veri sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin.  
  
2. Veri sözleşmelerinin yalnızca meta verilerinin oluşturulması gerektiğini belirtmek için `/dataContract` anahtarını kullanarak derlenmiş derlemelerde Svcutil. exe ' yi çalıştırın.  
  
    > [!NOTE]
    > Herhangi bir bağımlı derlemeye dosya yolunu `/reference` belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir basit hizmet uygulama ve yapılandırması için meta verilerin nasıl oluşturulacağını göstermektedir.  
  
 Hizmet sözleşmesinin meta verilerini dışarı aktarmak için.  
  
```  
svcutil.exe Contracts.dll  
```  
  
 Veri sözleşmelerinin meta verilerini dışarı aktarmak için.  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Hizmet uygulamasının meta verilerini dışarı aktarmak için.  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 , `<path>` Sözleşmelerin. dll yoludur.  
  
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

- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
