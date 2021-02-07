---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation Işlemlerine genel bakış'
title: Windows Communication Foundation İşlemleri Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: c9d251e4f49ee8e2edaa0ce2ff48738383a1b76c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752658"
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="c1ef0-103">Windows Communication Foundation İşlemleri Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1ef0-103">Windows Communication Foundation Transactions Overview</span></span>

<span data-ttu-id="c1ef0-104">İşlemler, bir dizi eylemin veya işlemin tek bir görünmeyen yürütme birimiyle gruplandırılmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-104">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="c1ef0-105">İşlem, aşağıdaki özelliklere sahip işlemler koleksiyonudur:</span><span class="sxs-lookup"><span data-stu-id="c1ef0-105">A transaction is a collection of operations with the following properties:</span></span>  
  
- <span data-ttu-id="c1ef0-106">Kararlılık.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-106">Atomicity.</span></span> <span data-ttu-id="c1ef0-107">Bu, belirli bir işlem altında tamamlanan tüm güncelleştirmelerin yapıldığından ve sürekli olarak yapıldığından ya da tümünün durdurulduğundan ve önceki durumlarına geri döndürüldüğünden emin olur.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-107">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
- <span data-ttu-id="c1ef0-108">Tutarlılık.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-108">Consistency.</span></span> <span data-ttu-id="c1ef0-109">Bu, bir işlem altında yapılan değişikliklerin, tutarlı bir durumdan diğerine dönüştürmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-109">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="c1ef0-110">Örneğin, bir denetim hesabından tasarruf hesabına para aktaran bir işlem, genel banka hesabındaki para miktarını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-110">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
- <span data-ttu-id="c1ef0-111">Yalıtım.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-111">Isolation.</span></span> <span data-ttu-id="c1ef0-112">Bu işlem, bir işlemin diğer eş zamanlı işlemlere ait kaydedilmemiş değişiklikleri gözlemmasını önler.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-112">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="c1ef0-113">Yalıtım bir eşzamanlılık soyutlaması sağlarken bir işlemin başka bir işlemin yürütülmesi üzerinde beklenmedik bir etkiye sahip olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-113">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
- <span data-ttu-id="c1ef0-114">Lığının.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-114">Durability.</span></span> <span data-ttu-id="c1ef0-115">Bu, bir kez kaydedildikten sonra yönetilen kaynaklardaki (veritabanı kaydı gibi) güncelleştirmelerin hatalara karşı kalıcı olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-115">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="c1ef0-116">Windows Communication Foundation (WCF), Web hizmeti uygulamanızda dağıtılmış işlemler oluşturmanızı sağlayan zengin bir özellik kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-116">Windows Communication Foundation (WCF) provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 <span data-ttu-id="c1ef0-117">WCF, WCF uygulamalarının işlemleri, üçüncü taraf teknoloji kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri gibi birlikte çalışabilme uygulamalarına akışını sağlayan WS-AtomicTransaction (WS-AT) protokolü için destek uygular.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-117">WCF implements support for the WS-AtomicTransaction (WS-AT) protocol that enables WCF applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> <span data-ttu-id="c1ef0-118">WCF Ayrıca, işlem akışını etkinleştirmek için birlikte çalışma işlevselliğine gerek duymayan senaryolarda kullanılabilen OLE Transactions protokolü için destek uygular.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-118">WCF also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="c1ef0-119">Bir uygulama yapılandırma dosyasını, işlem akışını etkinleştirmek veya devre dışı bırakmak için bağlamaları yapılandırmak ve bir bağlamada istenen işlem protokolünü ayarlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-119">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="c1ef0-120">Ayrıca, yapılandırma dosyasını kullanarak hizmet düzeyinde işlem zaman aşımlarını ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-120">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="c1ef0-121">Daha fazla bilgi için bkz. [Işlem akışını etkinleştirme](enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="c1ef0-121">For more information, see [Enabling Transaction Flow](enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="c1ef0-122">Ad alanındaki işlem öznitelikleri <xref:System.ServiceModel> şunları yapmanıza izin verir:</span><span class="sxs-lookup"><span data-stu-id="c1ef0-122">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
- <span data-ttu-id="c1ef0-123">Özniteliği kullanarak işlem zaman aşımları ve yalıtım düzeyinde filtreleme yapılandırın <xref:System.ServiceModel.ServiceBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c1ef0-123">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="c1ef0-124">İşlem işlevlerini etkinleştirin ve özniteliği kullanarak işlem tamamlama davranışını yapılandırın <xref:System.ServiceModel.OperationBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c1ef0-124">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="c1ef0-125"><xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> İşlem akışına izin vermek veya reddetmek için bir sözleşme yönteminde ve özniteliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-125">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="c1ef0-126">Daha fazla bilgi için bkz. [ServiceModel Işlem öznitelikleri](servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c1ef0-126">For more information, see [ServiceModel Transaction Attributes](servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ef0-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1ef0-127">See also</span></span>

- [<span data-ttu-id="c1ef0-128">ServiceModel İşlem Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c1ef0-128">ServiceModel Transaction Attributes</span></span>](servicemodel-transaction-attributes.md)
- [<span data-ttu-id="c1ef0-129">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c1ef0-129">Enabling Transaction Flow</span></span>](enabling-transaction-flow.md)
