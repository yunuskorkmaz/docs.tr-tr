---
title: Fabrika Modeline Genel Bakış
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 7d50ddd3b02b66a5b2be41eaba5cf9a497b5f1b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795080"
---
# <a name="factory-model-overview"></a>Fabrika Modeline Genel Bakış
ADO.NET 2,0, <xref:System.Data.Common> ad alanında yeni temel sınıflar sunmuştur. Taban sınıflar soyuttur, yani doğrudan örneklenemez. <xref:System.Data.Common.DbConnection> ,Ve<xref:System.Data.SqlClient> gibi .NET Framework veri sağlayıcıları<xref:System.Data.OleDb>tarafından paylaşılır. <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbDataAdapter> Temel sınıfların eklenmesi, yeni arabirimler oluşturmak zorunda kalmadan .NET Framework veri sağlayıcılarına işlevsellik eklenmesini basitleştirir.  
  
 ADO.NET 2,0, bir geliştiricinin belirli bir veri sağlayıcısına bağımlı olmayan genel veri erişim kodu yazmasını sağlayan soyut temel sınıflar da sunmuştur.  
  
## <a name="the-factory-design-pattern"></a>Fabrika tasarım kalıbı  
 Sağlayıcıdan bağımsız kod yazmak için programlama modeli, birden çok sağlayıcı genelinde veritabanlarına erişmek için tek bir API kullanan "fabrika" tasarım deseninin kullanımına dayanır. Bu model, gerçek bir fabrika gibi yalnızca diğer nesneleri oluşturmak için özel bir nesnenin kullanımını çağırdığı için oldukça adlandırılır. Fabrika tasarım deseninin daha ayrıntılı bir açıklaması için, bkz. [ASP.NET 2,0 ve ADO.NET 2,0 ' de genel veri erişim kodu yazma](https://go.microsoft.com/fwlink/?LinkId=55915).
  
 ADO.NET 2,0 ile <xref:System.Data.Common.DbProviderFactories> başlayarak, sınıfı bir <xref:System.Data.Common.DbProviderFactory> örnek `static` oluşturmak için `Shared` (veya Visual Basic) yöntemler sağlar. Örnek daha sonra sağlayıcı bilgilerine ve çalışma zamanında sağlanan bağlantı dizesine göre doğru bir kesin türü belirtilmiş nesne döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
