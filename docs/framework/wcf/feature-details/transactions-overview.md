---
title: "Windows Communication Foundation İşlemleri Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb90d0f93e9bdf7dd9779ffd5d4b1288ba56e7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="674f1-102">Windows Communication Foundation İşlemleri Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="674f1-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="674f1-103">İşlemler eylemler veya tek bir bölünemez birime işlemleri yürütme kümesini gruplamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="674f1-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="674f1-104">Bir işlem, aşağıdaki özelliklere sahip işlemleri koleksiyonudur:</span><span class="sxs-lookup"><span data-stu-id="674f1-104">A transaction is a collection of operations with the following properties:</span></span>  
  
-   <span data-ttu-id="674f1-105">Atom oranı.</span><span class="sxs-lookup"><span data-stu-id="674f1-105">Atomicity.</span></span> <span data-ttu-id="674f1-106">Bu, belirli bir işlem altında tamamlandı güncelleştirmelerini kaydedilen ve dayanıklı hale ya da bunlar tüm durduruldu ve önceki durumlarına geri olduğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="674f1-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="674f1-107">Tutarlılık.</span><span class="sxs-lookup"><span data-stu-id="674f1-107">Consistency.</span></span> <span data-ttu-id="674f1-108">Bu, bir işlem altında yapılan değişiklikleri tutarlı bir durumdan diğerine dönüştürme temsil ettiğini garanti eder.</span><span class="sxs-lookup"><span data-stu-id="674f1-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="674f1-109">Örneğin, para tasarrufu hesabına denetleme hesabından aktaran bir işlem genel banka hesabı para miktarını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="674f1-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
-   <span data-ttu-id="674f1-110">Yalıtım.</span><span class="sxs-lookup"><span data-stu-id="674f1-110">Isolation.</span></span> <span data-ttu-id="674f1-111">Bu, diğer eşzamanlı işlemler ait kaydedilmemiş değişiklikler Gözlemleme gelen bir işlem engeller.</span><span class="sxs-lookup"><span data-stu-id="674f1-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="674f1-112">Bir işlem sağlarken eşzamanlılık bir soyutlamasını başka bir işlemin yürütülmesi beklenmeyen bir etkiye sahip olamaz, yalıtım da sağlar.</span><span class="sxs-lookup"><span data-stu-id="674f1-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
-   <span data-ttu-id="674f1-113">Dayanıklılık.</span><span class="sxs-lookup"><span data-stu-id="674f1-113">Durability.</span></span> <span data-ttu-id="674f1-114">Bu tamamlandıktan sonra yönetilen kaynaklar (örneğin, bir veritabanı kaydını) güncelleştirmeleri hataları karşısında kalıcı olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="674f1-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="674f1-115">zengin bir Web hizmeti uygulamanız dağıtılmış işlemler oluşturmanıza olanak sağlayan özellikler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="674f1-115"> provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="674f1-116">etkinleştirir WS-AtomicTransaction (WS-AT) protokolü için desteği uygulayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar, üçüncü taraf teknolojisi kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri gibi birlikte çalışabilen uygulamaları akış işlemleri.</span><span class="sxs-lookup"><span data-stu-id="674f1-116"> implements support for the WS-AtomicTransaction (WS-AT) protocol that enables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="674f1-117">Ayrıca, burada işlem akışını etkinleştirmek için birlikte çalışma işlevselliği gerekmez senaryolarda kullanılabilir OLE hareketleri protokolü için desteği uygular.</span><span class="sxs-lookup"><span data-stu-id="674f1-117"> also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="674f1-118">Uygulama yapılandırma dosyası etkinleştirmek ya da işlem akışını devre dışı bırakmak, aynı zamanda bir bağlama üzerinde istenen işlem protokolü ayarlamak için bağlamalar yapılandırmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="674f1-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="674f1-119">Ayrıca, yapılandırma dosyası kullanarak hizmet düzeyinde işlem zaman aşımlarını ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="674f1-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="674f1-120">[İşlem akışını etkinleştirme](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="674f1-120"> [Enabling Transaction Flow](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="674f1-121">İşlem öznitelikleri <xref:System.ServiceModel> ad alanı, aşağıdakileri yapmak izin ver:</span><span class="sxs-lookup"><span data-stu-id="674f1-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
-   <span data-ttu-id="674f1-122">İşlem zaman aşımlarını ve yalıtım düzeyi kullanılarak filtrelemeyi yapılandırmak <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="674f1-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="674f1-123">İşlemler işlevselliğini etkinleştirmek ve işlem tamamlama davranışını kullanarak yapılandırma <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="674f1-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="674f1-124">Kullanım <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> gerektirecek şekilde bir sözleşme yöntemi özniteliklerinde izin verin veya işlem akışını reddedin.</span><span class="sxs-lookup"><span data-stu-id="674f1-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="674f1-125">[ServiceModel işlem öznitelikleri](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="674f1-125"> [ServiceModel Transaction Attributes](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="674f1-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="674f1-126">See Also</span></span>  
 [<span data-ttu-id="674f1-127">ServiceModel İşlem Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="674f1-127">ServiceModel Transaction Attributes</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [<span data-ttu-id="674f1-128">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="674f1-128">Enabling Transaction Flow</span></span>](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
