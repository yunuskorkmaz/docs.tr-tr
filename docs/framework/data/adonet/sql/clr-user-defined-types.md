---
title: CLR kullanıcı tanımlı türler
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: 344245ea7c67d7b5363c17bb42e2606ca11142bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357588"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="71ecd-102">CLR kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="71ecd-102">CLR User-Defined Types</span></span>
<span data-ttu-id="71ecd-103">Microsoft SQL Server, Microsoft .NET Framework ortak dil çalışma zamanı ile (CLR) uygulanan kullanıcı tanımlı türler (atama) için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="71ecd-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="71ecd-104">CLR SQL Server'a tümleşiktir ve bu düzenek veritabanının tür sistemi genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="71ecd-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="71ecd-105">Atama kullanıcı genişletilebilirlik SQL Server veri türü sisteminin ve karmaşık yapılandırılmış türleri tanımlama yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="71ecd-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="71ecd-106">Atama bir uygulama mimarisi açısından iki temel fayda sağlar:</span><span class="sxs-lookup"><span data-stu-id="71ecd-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="71ecd-107">Güçlü kapsülleme (hem de istemci ve sunucu) iç durum ve dış davranışları arasında.</span><span class="sxs-lookup"><span data-stu-id="71ecd-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="71ecd-108">Diğer derin tümleştirme server özellikleri ilgili.</span><span class="sxs-lookup"><span data-stu-id="71ecd-108">Deep integration with other related server features.</span></span> <span data-ttu-id="71ecd-109">Kendi UDT tanımladıktan sonra burada sütun tanımları dahil olmak üzere SQL Server'da ve değişkenleri, parametreleri, işlevi sonuçları, imleçler, tetikleyiciler ve çoğaltma olarak bir sistem türü kullanabilirsiniz tüm bağlamlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71ecd-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="71ecd-110">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="71ecd-110">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="71ecd-111">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="71ecd-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="71ecd-112">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="71ecd-112">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a><span data-ttu-id="71ecd-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71ecd-113">See Also</span></span>  
 [<span data-ttu-id="71ecd-114">Yönetilen kodda SQL Server 2005'te nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="71ecd-114">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="71ecd-115">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="71ecd-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
