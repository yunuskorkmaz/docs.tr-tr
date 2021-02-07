---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: meta verileri derlenmiş hizmet kodundan dışarı aktarmak için Svcutil.exe kullanma'
title: 'Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 509d987ff27f9a05ca59d6065d76f27006f3cb25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734210"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma

Svcutil.exe, derlenmiş derlemelerde hizmetler, sözleşmeler ve veri türleri için meta verileri aşağıdaki gibi dışarı aktarabilir:  
  
- Svcutil.exe kullanarak bir derleme kümesi için derlenen tüm hizmet sözleşmelerinin meta verilerini dışa aktarmak için, derlemeleri giriş parametresi olarak belirtin. Bu, varsayılan davranıştır.  
  
- Svcutil.exe kullanarak derlenmiş bir hizmetin meta verilerini dışarı aktarmak için, hizmet derleme veya derlemeleri giriş parametresi olarak belirtin. `/serviceName`Dışarı aktarmak istediğiniz hizmetin yapılandırma adını belirtmek için seçeneğini kullanmanız gerekir. Svcutil.exe, belirtilen yürütülebilir derleme için yapılandırma dosyasını otomatik olarak yükler.  
  
- Bir derleme kümesi içindeki tüm veri anlaşması türlerini dışarı aktarmak için `/dataContractOnly` seçeneğini kullanın.  
  
> [!NOTE]
> `/reference`Herhangi bir bağımlı derlemeye dosya yollarını belirtmek için seçeneğini kullanın.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Derlenmiş hizmet sözleşmeleri için meta verileri dışarı aktarmak için  
  
1. Hizmet sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin. 1  
  
2. Derlenmiş derlemelerde Svcutil.exe çalıştırın.  
  
    > [!NOTE]
    > `/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```console
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
  
3. `/serviceName`Hizmetin yapılandırma adını belirtmek için anahtarı kullanarak derlenmiş hizmet yürütülebilir dosyası üzerinde Svcutil.exe çalıştırın.  
  
    > [!NOTE]
    > `/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Derlenen veri sözleşmeleri için meta verileri dışarı aktarmak için  
  
1. Veri sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin.  
  
2. `/dataContract`Yalnızca veri sözleşmeleri için meta verilerin oluşturulması gerektiğini belirtmek için anahtarını kullanarak derlenmiş derlemelerde Svcutil.exe çalıştırın.  
  
    > [!NOTE]
    > `/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir basit hizmet uygulama ve yapılandırması için meta verilerin nasıl oluşturulacağını göstermektedir.  
  
 Hizmet sözleşmesinin meta verilerini dışarı aktarmak için.  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 Veri sözleşmelerinin meta verilerini dışarı aktarmak için.  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Hizmet uygulamasının meta verilerini dışarı aktarmak için.  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 , `<path>` Contracts.dll yoludur.  
  
```csharp
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
```

```csharp
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
```

```xml  
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

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](exporting-and-importing-metadata.md)
