---
title: İşlem Modelleri
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 2d3d0631c47506e7bd99d90ed49a1fdc76cc7a59
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556830"
---
# <a name="transaction-models"></a><span data-ttu-id="2ca4c-102">İşlem Modelleri</span><span class="sxs-lookup"><span data-stu-id="2ca4c-102">Transaction Models</span></span>
<span data-ttu-id="2ca4c-103">Bu konu, işlem programlama modelleri ile Microsoft 'un sağladığı altyapı bileşenleri arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="2ca4c-104">Windows Communication Foundation (WCF) ' de işlemleri kullanırken, farklı işlem modelleri arasında seçim olmadığınızı, ancak tümleşik ve tutarlı bir modelin farklı katmanlarında çalıştığını anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="2ca4c-105">Aşağıdaki bölümlerde, üç birincil işlem bileşeni açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="2ca4c-106">Windows Communication Foundation Işlemler</span><span class="sxs-lookup"><span data-stu-id="2ca4c-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="2ca4c-107">WCF 'de işlem desteği, işlem hizmetleri yazmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="2ca4c-108">Ayrıca, WS-AtomicTransaction (WS-AT) protokolü desteğiyle, uygulamalar, WCF veya üçüncü taraf teknolojisi kullanılarak oluşturulan Web hizmetlerine işlemleri akabilir.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="2ca4c-109">WCF hizmeti veya uygulamasında, WCF işlem özellikleri, altyapının işlem oluşturma, akış ve zaman eşitlemesini nasıl ve ne zaman bir şekilde kullandığını bildirimli olarak, öznitelikler ve yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="2ca4c-110">System. Transactions Işlemleri</span><span class="sxs-lookup"><span data-stu-id="2ca4c-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="2ca4c-111"><xref:System.Transactions>Ad alanı, sınıfını temel alan açık bir programlama modeli <xref:System.Transactions.Transaction> ve ayrıca <xref:System.Transactions.TransactionScope> altyapının işlemleri otomatik olarak yönettiği sınıfını kullanan örtülü bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="2ca4c-112">Bu iki modeli kullanarak bir işlem uygulamasının nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [bir Işlem uygulaması yazma](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="2ca4c-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="2ca4c-113">Bir WCF hizmetinde veya uygulamada, <xref:System.Transactions> bir istemci uygulaması içinde işlem oluşturmak ve gerektiğinde bir işlemle birlikte etkileşim kurmak için programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="2ca4c-114">MSDTC Işlemleri</span><span class="sxs-lookup"><span data-stu-id="2ca4c-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="2ca4c-115">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC), dağıtılmış işlemler için destek sağlayan bir işlem yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="2ca4c-116">Daha fazla bilgi için bkz. [DTC programlayıcı başvurusu](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2ca4c-116">For more information, see the [DTC Programmer's Reference](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="2ca4c-117">Bir WCF hizmetinde veya uygulamada, MSDTC, bir istemci veya hizmet içinde oluşturulan işlemlerin koordinasyonu için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ca4c-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
