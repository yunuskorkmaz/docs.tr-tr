---
title: 'Nasıl yapılır: Bağlantı Dizesi Tanımlama'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854652"
---
# <a name="how-to-define-the-connection-string"></a>Nasıl yapılır: Bağlantı Dizesi Tanımlama

Bu konu başlığı altında, kavramsal bir modele bağlanırken kullanılan bağlantı dizesinin nasıl tanımlanacağı gösterilmektedir. Bu konu, [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) kavramsal modeline dayalıdır. AdventureWorks Sales modeli, Entity Framework belgelerindeki görevle ilgili konular boyunca kullanılır. Bu konu, Entity Framework yapılandırdığınız ve AdventureWorks Sales modelini tanımladığınız varsayılmaktadır. Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))el ile tanımlayın. Bu konudaki [yordamlar, nasıl yapılır: Entity Framework projesini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))el ile yapılandırın.

> [!NOTE]
> Visual Studio projesinde Varlık Veri Modeli Sihirbazı 'nı kullanırsanız, otomatik olarak bir. edmx dosyası oluşturur ve projeyi Entity Framework kullanacak şekilde yapılandırır. Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı 'nı kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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

- [Hızlı başlangıç](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Nasıl yapılır: Yeni bir. edmx dosyası oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
