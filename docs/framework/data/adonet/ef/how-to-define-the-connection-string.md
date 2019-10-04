---
title: 'Nasıl yapılır: bağlantı dizesini tanımlama'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833946"
---
# <a name="how-to-define-the-connection-string"></a>Nasıl yapılır: bağlantı dizesini tanımlama

Bu konu başlığı altında, kavramsal bir modele bağlanırken kullanılan bağlantı dizesinin nasıl tanımlanacağı gösterilmektedir. Bu konu, [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) kavramsal modeline dayalıdır. AdventureWorks Sales modeli, Entity Framework belgelerindeki görevle ilgili konular boyunca kullanılır. Bu konu, Entity Framework yapılandırdığınız ve AdventureWorks Sales modelini tanımladığınız varsayılmaktadır. Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını el Ile tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Bu konudaki yordamlar, [nasıl yapılır: el ile Entity Framework projesi yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))bölümüne de eklenmiştir.

> [!NOTE]
> Visual Studio projesinde Varlık Veri Modeli Sihirbazı 'nı kullanırsanız, otomatik olarak bir. edmx dosyası oluşturur ve projeyi Entity Framework kullanacak şekilde yapılandırır. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

## <a name="to-define-the-entity-framework-connection-string"></a>Entity Framework bağlantı dizesini tanımlamak için

- Projenin uygulama yapılandırma dosyasını (App. config) açın ve aşağıdaki bağlantı dizesini ekleyin:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Projenizde bir uygulama yapılandırma dosyası yoksa, **Proje** menüsünde **Yeni öğe Ekle** ' yi seçerek, **genel** kategorisini seçerek, **uygulama yapılandırma dosyası**' nı seçip ardından **Ekleyin**.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Nasıl yapılır: yeni bir. edmx dosyası oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
