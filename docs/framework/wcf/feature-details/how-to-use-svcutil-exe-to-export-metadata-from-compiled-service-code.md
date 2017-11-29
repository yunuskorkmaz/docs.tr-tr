---
title: "Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 444fab903683b952d1a8c312c3f6032be880da68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma
Svcutil.exe gibi hizmetleri, sözleşmeler ve derlenmiş derlemelerde veri türlerini için meta verileri dışarı aktarabilirsiniz:  
  
-   Tüm meta verilerini aktarmak için Svcutil.exe, kullanarak derlemeler kümesi için hizmet sözleşmeleri derlenmiş giriş parametreleri olarak derlemeler belirtin. Bu varsayılan davranıştır.  
  
-   Svcutil.exe kullanarak derlenmiş bir hizmet için meta verileri dışarı aktarmak için hizmet derleme veya derlemelerin giriş parametreleri olarak belirtin. Kullanmalısınız `/serviceName` vermek istediğiniz hizmet yapılandırma adını belirtmek için seçeneği. Svcutil.exe yapılandırma dosyası için belirtilen çalıştırılabilir derlemeyi otomatik olarak yükler.  
  
-   Derlemeler kümesini içindeki tüm veri sözleşme türleri dışarı aktarmak için kullanın `/dataContractOnly` seçeneği.  
  
> [!NOTE]
>  Kullanım `/reference` seçeneği tüm bağımlı derlemeler için dosya yolunu belirtin.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Meta verileri derlenmiş Hizmet sözleşmeleri için dışarı aktarmak için  
  
1.  Bir veya daha fazla sınıf libraries.1 halinde, hizmet sözleşmesi uygulamaları derleme  
  
2.  Svcutil.exe derlenmiş derlemelerini çalıştırın.  
  
    > [!NOTE]
    >  Kullanmanız gerekebilir `/reference` anahtar herhangi bir bağımlı derleme dosya yolunu belirtin.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Derlenmiş bir hizmet için meta verileri dışarı aktarmak için  
  
1.  Yürütülebilir bir bütünleştirilmiş hizmet uygulamanızı derleyin.  
  
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
  
3.  Svcutil.exe derlenmiş hizmet yürütülebilir kullanarak çalıştırın `/serviceName` anahtar hizmetin yapılandırma adını belirtin.  
  
    > [!NOTE]
    >  Kullanmanız gerekebilir `/reference` anahtar herhangi bir bağımlı derleme dosya yolunu belirtin.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Derlenmiş veri sözleşmeleri için meta verileri dışarı aktarmak için  
  
1.  Veri sözleşmesi uygulamaları bir veya daha fazla sınıf kitaplıkları içine derleyin.  
  
2.  Kullanarak derlenmiş derlemeler svcutil.exe çalıştırmak `/dataContract` yalnızca meta verilerin veri sözleşmeleri üretilmesi gerektiğini belirtmek için anahtar.  
  
    > [!NOTE]
    >  Kullanmanız gerekebilir `/reference` anahtar herhangi bir bağımlı derleme dosya yolunu belirtin.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir basit hizmeti uygulama ve yapılandırma meta verilerini oluşturmak gösterilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Meta veri alma ve verme](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
