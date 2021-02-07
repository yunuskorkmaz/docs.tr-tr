---
description: 'Daha fazla bilgi edinin: fabrika modeline genel bakış'
title: Fabrika Modeline Genel Bakış
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 175b05a298eb260dfe8c59b380ab3b8b9dcba943
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724212"
---
# <a name="factory-model-overview"></a><span data-ttu-id="d0767-103">Fabrika Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0767-103">Factory Model Overview</span></span>

<span data-ttu-id="d0767-104">ADO.NET 2,0, ad alanında yeni temel sınıflar sunmuştur <xref:System.Data.Common> .</span><span class="sxs-lookup"><span data-stu-id="d0767-104">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="d0767-105">Taban sınıflar soyuttur, yani doğrudan örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="d0767-105">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="d0767-106">, Ve <xref:System.Data.Common.DbConnection> gibi <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbDataAdapter> .NET Framework veri sağlayıcıları tarafından paylaşılır <xref:System.Data.SqlClient> <xref:System.Data.OleDb> .</span><span class="sxs-lookup"><span data-stu-id="d0767-106">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="d0767-107">Temel sınıfların eklenmesi, yeni arabirimler oluşturmak zorunda kalmadan .NET Framework veri sağlayıcılarına işlevsellik eklenmesini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="d0767-107">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="d0767-108">ADO.NET 2,0, bir geliştiricinin belirli bir veri sağlayıcısına bağımlı olmayan genel veri erişim kodu yazmasını sağlayan soyut temel sınıflar da sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="d0767-108">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="d0767-109">Fabrika tasarım kalıbı</span><span class="sxs-lookup"><span data-stu-id="d0767-109">The Factory Design Pattern</span></span>  

 <span data-ttu-id="d0767-110">Sağlayıcıdan bağımsız kod yazmak için programlama modeli, birden çok sağlayıcı genelinde veritabanlarına erişmek için tek bir API kullanan "fabrika" tasarım deseninin kullanımına dayanır.</span><span class="sxs-lookup"><span data-stu-id="d0767-110">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="d0767-111">Bu model, gerçek bir fabrika gibi yalnızca diğer nesneleri oluşturmak için özel bir nesnenin kullanımını çağırdığı için oldukça adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d0767-111">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="d0767-112">Fabrika tasarım deseninin daha ayrıntılı bir açıklaması için, bkz. [ASP.NET 2,0 ve ADO.NET 2,0 ' de genel veri erişim kodu yazma](/previous-versions/dotnet/articles/ms971499(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="d0767-112">For a more detailed description of the factory design pattern, see [Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](/previous-versions/dotnet/articles/ms971499(v=msdn.10)).</span></span>
  
 <span data-ttu-id="d0767-113">ADO.NET 2,0 ile başlayarak, <xref:System.Data.Common.DbProviderFactories> sınıfı `static` `Shared` bir örnek oluşturmak için (veya Visual Basic) yöntemler sağlar <xref:System.Data.Common.DbProviderFactory> .</span><span class="sxs-lookup"><span data-stu-id="d0767-113">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="d0767-114">Örnek daha sonra sağlayıcı bilgilerine ve çalışma zamanında sağlanan bağlantı dizesine göre doğru bir kesin türü belirtilmiş nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0767-114">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0767-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0767-115">See also</span></span>

- [<span data-ttu-id="d0767-116">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="d0767-116">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="d0767-117">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="d0767-117">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="d0767-118">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d0767-118">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="d0767-119">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0767-119">ADO.NET Overview</span></span>](ado-net-overview.md)
