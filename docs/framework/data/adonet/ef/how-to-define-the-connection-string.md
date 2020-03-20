---
title: 'Nasıl yapılır: Bağlantı Dizesi Tanımlama'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150577"
---
# <a name="how-to-define-the-connection-string"></a>Nasıl yapılır: Bağlantı Dizesi Tanımlama

Bu konu, kavramsal bir modele bağlanırken kullanılan bağlantı dizesinin nasıl tanımlandığını gösterir. Bu konu [AdventureWorks Satış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) kavramsal modeline dayanmaktadır. AdventureWorks Satış Modeli, Entity Framework belgelerinde görevle ilgili konular boyunca kullanılır. Bu konu, Varlık Çerçevesi'ni zaten yapılandırdığınızı ve AdventureWorks Satış Modelini tanımladığınızı varsayar. Daha fazla bilgi için [bkz: Modeli el ile tanımla ve Dosyaları Eşleme.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)) Bu konudaki yordamlar, Nasıl [Yapılır: Varlık Çerçeve Projesi'ni el ile yapılandırın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))

> [!NOTE]
> Visual Studio projesinde Varlık Veri Modeli Sihirbazı'nı kullanırsanız, otomatik olarak bir .edmx dosyası oluşturur ve projeyi Varlık Çerçevesi'ni kullanacak şekilde yapılandırır. Daha fazla bilgi için [bkz: Varlık Veri Modeli Sihirbazı'nı kullanın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

## <a name="to-define-the-entity-framework-connection-string"></a>Varlık Çerçevesi bağlantı dizesini tanımlamak için

- Projenin uygulama yapılandırma dosyasını (app.config) açın ve aşağıdaki bağlantı dizesini ekleyin:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Projenizde bir uygulama yapılandırma dosyası yoksa, **Proje** menüsünden **Yeni Öğe Ekle'yi** seçerek, **Genel** kategoriyi seçerek, Uygulama **Yapılandırma Dosyası'nı**seçerek ve sonra **Ekle'yi**tıklatarak bir tane ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Nasıl Yapılsın: Yeni .edmx Dosyası Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Varlık Veri Modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
