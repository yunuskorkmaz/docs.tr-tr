---
title: Fabrika Modeline Genel Bakış
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: c3d4680e91feb650ea061f56dc72bf032b7b5e15
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540920"
---
# <a name="factory-model-overview"></a>Fabrika Modeline Genel Bakış
ADO.NET 2,0, ad alanında yeni temel sınıflar sunmuştur <xref:System.Data.Common> . Taban sınıflar soyuttur, yani doğrudan örneklenemez. , Ve <xref:System.Data.Common.DbConnection> gibi <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbDataAdapter> .NET Framework veri sağlayıcıları tarafından paylaşılır <xref:System.Data.SqlClient> <xref:System.Data.OleDb> . Temel sınıfların eklenmesi, yeni arabirimler oluşturmak zorunda kalmadan .NET Framework veri sağlayıcılarına işlevsellik eklenmesini basitleştirir.  
  
 ADO.NET 2,0, bir geliştiricinin belirli bir veri sağlayıcısına bağımlı olmayan genel veri erişim kodu yazmasını sağlayan soyut temel sınıflar da sunmuştur.  
  
## <a name="the-factory-design-pattern"></a>Fabrika tasarım kalıbı  
 Sağlayıcıdan bağımsız kod yazmak için programlama modeli, birden çok sağlayıcı genelinde veritabanlarına erişmek için tek bir API kullanan "fabrika" tasarım deseninin kullanımına dayanır. Bu model, gerçek bir fabrika gibi yalnızca diğer nesneleri oluşturmak için özel bir nesnenin kullanımını çağırdığı için oldukça adlandırılır. Fabrika tasarım deseninin daha ayrıntılı bir açıklaması için, bkz. [ASP.NET 2,0 ve ADO.NET 2,0 ' de genel veri erişim kodu yazma](/previous-versions/dotnet/articles/ms971499(v=msdn.10)).
  
 ADO.NET 2,0 ile başlayarak, <xref:System.Data.Common.DbProviderFactories> sınıfı `static` `Shared` bir örnek oluşturmak için (veya Visual Basic) yöntemler sağlar <xref:System.Data.Common.DbProviderFactory> . Örnek daha sonra sağlayıcı bilgilerine ve çalışma zamanında sağlanan bağlantı dizesine göre doğru bir kesin türü belirtilmiş nesne döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
