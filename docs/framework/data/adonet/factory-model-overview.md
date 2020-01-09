---
title: Fabrika Modeline Genel Bakış
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: f344502453acbbb5c08e49b7c21a0f4e84a29ffa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348392"
---
# <a name="factory-model-overview"></a>Fabrika Modeline Genel Bakış
ADO.NET 2,0 <xref:System.Data.Common> ad alanına yeni temel sınıflar getirmiştir. Taban sınıflar soyuttur, yani doğrudan örneklenemez. <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>ve <xref:System.Data.Common.DbDataAdapter> içerirler ve <xref:System.Data.SqlClient> ve <xref:System.Data.OleDb>gibi .NET Framework veri sağlayıcıları tarafından paylaşılır. Temel sınıfların eklenmesi, yeni arabirimler oluşturmak zorunda kalmadan .NET Framework veri sağlayıcılarına işlevsellik eklenmesini basitleştirir.  
  
 ADO.NET 2,0, bir geliştiricinin belirli bir veri sağlayıcısına bağımlı olmayan genel veri erişim kodu yazmasını sağlayan soyut temel sınıflar da sunmuştur.  
  
## <a name="the-factory-design-pattern"></a>Fabrika tasarım kalıbı  
 Sağlayıcıdan bağımsız kod yazmak için programlama modeli, birden çok sağlayıcı genelinde veritabanlarına erişmek için tek bir API kullanan "fabrika" tasarım deseninin kullanımına dayanır. Bu model, gerçek bir fabrika gibi yalnızca diğer nesneleri oluşturmak için özel bir nesnenin kullanımını çağırdığı için oldukça adlandırılır. Fabrika tasarım deseninin daha ayrıntılı bir açıklaması için, bkz. [ASP.NET 2,0 ve ADO.NET 2,0 ' de genel veri erişim kodu yazma](https://docs.microsoft.com/previous-versions/dotnet/articles/ms971499(v=msdn.10)).
  
 ADO.NET 2,0 ile başlayarak <xref:System.Data.Common.DbProviderFactories> sınıfı, <xref:System.Data.Common.DbProviderFactory> örnek oluşturmak için `static` (veya `Shared` Visual Basic) yöntemlerine sahiptir. Örnek daha sonra sağlayıcı bilgilerine ve çalışma zamanında sağlanan bağlantı dizesine göre doğru bir kesin türü belirtilmiş nesne döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
