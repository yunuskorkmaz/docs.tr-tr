---
title: "İşlem Modelleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c74b1826ca280ba05420449758cdbb84dac3e93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-models"></a><span data-ttu-id="0ff3f-102">İşlem Modelleri</span><span class="sxs-lookup"><span data-stu-id="0ff3f-102">Transaction Models</span></span>
<span data-ttu-id="0ff3f-103">Bu konu, işlem programlama modelleri ve Microsoft'un sağladığı altyapı bileşenleri arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="0ff3f-104">İşlemlerde kullanırken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], farklı işlem modelleri arasında seçmezseniz, ancak bunun yerine tümleşik ve tutarlı bir modeli farklı katmanlar işletim olduğunu anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-104">When using transactions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="0ff3f-105">Aşağıdaki bölümlerde üç birincil hareket bileşenlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="0ff3f-106">Windows Communication Foundation işlemleri</span><span class="sxs-lookup"><span data-stu-id="0ff3f-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="0ff3f-107">İşlem desteği, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlem Hizmetleri yazma sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-107">The transaction support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you write transactional services.</span></span> <span data-ttu-id="0ff3f-108">Ayrıca, WS-AtomicTransaction (WS-AT) protokolü için kendi desteği ile uygulamaları işlemleri kullanarak yerleşik Web hizmetlerine akabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veya üçüncü taraf teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or third-party technology.</span></span>  
  
 <span data-ttu-id="0ff3f-109">İçinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet veya uygulama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] öznitelikleri ve bildirimli olarak nasıl ve ne zaman altyapı oluşturmak, akış ve işlemleri eşitlemek belirtmek için yapılandırma işlem özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-109">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="0ff3f-110">System.Transactions işlemleri</span><span class="sxs-lookup"><span data-stu-id="0ff3f-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="0ff3f-111"><xref:System.Transactions> Ad alanı, temel alan hem bir açık programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı yanı sıra örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> içinde altyapı otomatik olarak yönetir işlemleri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="0ff3f-112">Bu iki modeli kullanarak bir işlem uygulaması oluşturmak için bkz: nasıl [işlem uygulaması yazma](http://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="0ff3f-112"> how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="0ff3f-113">İçinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet veya uygulama <xref:System.Transactions> hareketleri içinde bir istemci uygulaması oluşturmak ve gerektiğinde, hizmet içinde açıkça bir işlem ile etkileşmek için programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-113">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="0ff3f-114">MSDTC işlemleri</span><span class="sxs-lookup"><span data-stu-id="0ff3f-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="0ff3f-115">Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dağıtılmış işlemler için destek sağlayan bir işlem yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="0ff3f-116">[DTC Programcının Başvurusu](http://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="0ff3f-116"> the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="0ff3f-117">İçinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet veya uygulama, MSDTC gerekli altyapıyı sunar. bir istemci veya hizmet içinde oluşturulan işlem koordinasyonu için.</span><span class="sxs-lookup"><span data-stu-id="0ff3f-117">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
