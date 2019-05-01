---
title: İşlem Modelleri
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050785"
---
# <a name="transaction-models"></a><span data-ttu-id="1373e-102">İşlem Modelleri</span><span class="sxs-lookup"><span data-stu-id="1373e-102">Transaction Models</span></span>
<span data-ttu-id="1373e-103">Bu konuda, işlem programlama modelleri ve Microsoft'un sağladığı altyapı bileşenleri arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1373e-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="1373e-104">İşlemleri Windows Communication Foundation (WCF) kullanırken, farklı işlem modelleri arasında belirlenmemesi, ancak bunun yerine, tümleşik ve tutarlı bir modeli farklı katmanına işletim olduğunu anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1373e-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="1373e-105">Aşağıdaki bölümlerde, üç birincil işlem bileşeni açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1373e-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="1373e-106">Windows Communication Foundation işlemleri</span><span class="sxs-lookup"><span data-stu-id="1373e-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="1373e-107">İşlem desteği, WCF işlem hizmetlerinizi yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1373e-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="1373e-108">Ayrıca, WS-AtomicTransaction (WS-AT) protokolü için kendi destek ile uygulamaların WCF ya da üçüncü taraf teknolojisi kullanılarak oluşturulan Web Hizmetleri için işlem akabilir.</span><span class="sxs-lookup"><span data-stu-id="1373e-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="1373e-109">Bir WCF hizmeti veya uygulaması, WCF işlem özellikleri öznitelikleri ve bildirimli olarak nasıl ve ne zaman altyapı oluşturmak, akış ve eşitleme işlemleri belirtmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1373e-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="1373e-110">System.Transactions işlem</span><span class="sxs-lookup"><span data-stu-id="1373e-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="1373e-111"><xref:System.Transactions> Ad alanı, temel hem bir açık bir programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı, aynı zamanda örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> , altyapı otomatik olarak yönetir işlemleri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1373e-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="1373e-112">Bu iki modeli kullanarak bir işlem uygulama oluşturma hakkında daha fazla bilgi için bkz. [bir işlem uygulama yazma](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="1373e-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="1373e-113">Bir WCF hizmeti veya uygulamayı <xref:System.Transactions> hareketleri içinde bir istemci uygulaması oluşturma ve gerektiğinde, hizmet içinde bir işlem ile açıkça etkileşim kurmak için kullanabileceğiniz bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="1373e-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="1373e-114">MSDTC işlem</span><span class="sxs-lookup"><span data-stu-id="1373e-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="1373e-115">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dağıtılmış işlemler için destek sağlayan bir işlem yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="1373e-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="1373e-116">Daha fazla bilgi için [DTC Programcının Başvurusu](https://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="1373e-116">For more information, see the [DTC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="1373e-117">Bir WCF hizmeti veya uygulamayı MSDTC koordinasyonu bir istemci veya hizmet içinde oluşturulan işlem için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1373e-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
