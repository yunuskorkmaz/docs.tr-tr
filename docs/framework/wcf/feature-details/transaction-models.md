---
title: İşlem Modelleri
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499030"
---
# <a name="transaction-models"></a><span data-ttu-id="32ca6-102">İşlem Modelleri</span><span class="sxs-lookup"><span data-stu-id="32ca6-102">Transaction Models</span></span>
<span data-ttu-id="32ca6-103">Bu konu, işlem programlama modelleri ve Microsoft'un sağladığı altyapı bileşenleri arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="32ca6-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="32ca6-104">İşlemleri Windows Communication Foundation (WCF) kullanırken, farklı işlem modelleri arasında seçmezseniz, ancak bunun yerine tümleşik ve tutarlı bir modeli farklı katmanlar işletim olduğunu anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="32ca6-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="32ca6-105">Aşağıdaki bölümlerde üç birincil hareket bileşenlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="32ca6-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="32ca6-106">Windows Communication Foundation işlemleri</span><span class="sxs-lookup"><span data-stu-id="32ca6-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="32ca6-107">İşlem desteği, WCF işlem Hizmetleri yazma sağlar.</span><span class="sxs-lookup"><span data-stu-id="32ca6-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="32ca6-108">Ayrıca, WS-AtomicTransaction (WS-AT) protokolü için kendi desteği ile uygulamaları WCF veya üçüncü taraf teknolojisi kullanılarak oluşturulmuş Web hizmetlerine işlemleri akabilir.</span><span class="sxs-lookup"><span data-stu-id="32ca6-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="32ca6-109">Bir WCF hizmeti veya uygulamayı WCF işlem özellikleri öznitelikleri ve bildirimli olarak nasıl ve ne zaman altyapı oluşturmak, akış ve işlemleri eşitlemek belirtmek için yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="32ca6-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="32ca6-110">System.Transactions işlemleri</span><span class="sxs-lookup"><span data-stu-id="32ca6-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="32ca6-111"><xref:System.Transactions> Ad alanı, temel alan hem bir açık programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı yanı sıra örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> içinde altyapı otomatik olarak yönetir işlemleri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="32ca6-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="32ca6-112">Bu iki modeli kullanarak bir işlem uygulaması oluşturma hakkında daha fazla bilgi için bkz: [işlem uygulaması yazma](http://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="32ca6-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="32ca6-113">Bir WCF hizmeti veya uygulamayı <xref:System.Transactions> hareketleri içinde bir istemci uygulaması oluşturmak ve gerektiğinde, hizmet içinde açıkça bir işlem ile etkileşmek için programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="32ca6-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="32ca6-114">MSDTC işlemleri</span><span class="sxs-lookup"><span data-stu-id="32ca6-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="32ca6-115">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dağıtılmış işlemler için destek sağlayan bir işlem yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="32ca6-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="32ca6-116">Daha fazla bilgi için bkz: [DTC Programcının Başvurusu](http://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="32ca6-116">For more information, see the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="32ca6-117">Bir WCF hizmeti veya uygulamayı MSDTC bir istemci veya hizmet içinde oluşturulan işlem koordinasyonu için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="32ca6-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
