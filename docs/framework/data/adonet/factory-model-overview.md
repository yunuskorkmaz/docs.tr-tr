---
title: "Fabrika modeline genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0194cd6789ae6ddebeeee65abf1a4fca4a2bc0d6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="factory-model-overview"></a><span data-ttu-id="979a4-102">Fabrika modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="979a4-102">Factory Model Overview</span></span>
<span data-ttu-id="979a4-103">ADO.NET 2.0 sunulan yeni temel sınıflarda <xref:System.Data.Common> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="979a4-103">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="979a4-104">Temel sınıflar soyut, bunlar doğrudan başlatılamaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="979a4-104">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="979a4-105">İçerirler <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, ve <xref:System.Data.Common.DbDataAdapter> ve .NET Framework veri sağlayıcıları tarafından aşağıdaki gibi paylaşılan <xref:System.Data.SqlClient> ve <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="979a4-105">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="979a4-106">Temel sınıflar eklenmesi, yeni arabirimleri oluşturmak zorunda kalmadan .NET Framework Veri sağlayıcılarına ekleme işlevselliği basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="979a4-106">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="979a4-107">ADO.NET 2.0 ayrıca belirli veri sağlayıcısında bağlı olmayan bir genel veri erişim kodu yazmak bir geliştirici etkinleştirmek soyut taban sınıfları sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="979a4-107">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="979a4-108">Fabrika tasarım deseni</span><span class="sxs-lookup"><span data-stu-id="979a4-108">The Factory Design Pattern</span></span>  
 <span data-ttu-id="979a4-109">Sağlayıcı bağımsız kod yazmak için programlama modelini arasında birden çok sağlayıcı access veritabanları için tek bir API kullanır "fabrika" tasarım deseni kullanımını temel alır.</span><span class="sxs-lookup"><span data-stu-id="979a4-109">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="979a4-110">Yalnızca bir gerçek fabrikası gibi diğer nesneler oluşturmak için özel bir nesne kullanımı için çağırır gibi bu deseni aptly adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="979a4-110">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="979a4-111">Fabrika tasarım deseni daha ayrıntılı bir açıklaması için bkz: "[ASP.NET 2.0 ve ADO.NET 2.0 genel veri erişim kod yazma](http://go.microsoft.com/fwlink/?LinkId=55915)" ve "Genel kodlama ile ADO.NET 2.0 taban sınıfları ve oluşturucuları" [http:// MSDN.microsoft.com/library/default.asp?url=/library/dnvs05/HTML/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="979a4-111">For a more detailed description of the factory design pattern, see "[Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" and "Generic Coding with the ADO.NET 2.0 Base Classes and Factories" [http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) on MSDN.</span></span>  
  
 <span data-ttu-id="979a4-112">ADO.NET 2.0 ile başlayan <xref:System.Data.Common.DbProviderFactories> SAX `static` (veya `Shared` Visual Basic'te) oluşturmak için yöntemler bir <xref:System.Data.Common.DbProviderFactory> örneği.</span><span class="sxs-lookup"><span data-stu-id="979a4-112">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="979a4-113">Örnek ardından sağlayıcı bilgilerini ve çalışma zamanında sağlanan bağlantı dizesi göre doğru kesin türü belirtilmiş bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="979a4-113">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979a4-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="979a4-114">See Also</span></span>  
 [<span data-ttu-id="979a4-115">DbProviderFactory Alma</span><span class="sxs-lookup"><span data-stu-id="979a4-115">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="979a4-116">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="979a4-116">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="979a4-117">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="979a4-117">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="979a4-118">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="979a4-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
