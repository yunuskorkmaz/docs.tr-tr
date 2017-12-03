---
title: "İşlem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a6dcd11d34f0b81d6d3982ef1c6ab211d94818b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-processing"></a><span data-ttu-id="b28c0-102">İşlem</span><span class="sxs-lookup"><span data-stu-id="b28c0-102">Transaction Processing</span></span>
<span data-ttu-id="b28c0-103">Bir çevrimiçi bir kitaplığı defterinden satın aldığınızda, bir kitap (kredi biçiminde) karşılığında exchange.</span><span class="sxs-lookup"><span data-stu-id="b28c0-103">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="b28c0-104">Kredi iyi ise, bir dizi ilgili operations defteri alma ve kitaplığı, para alır sağlar.</span><span class="sxs-lookup"><span data-stu-id="b28c0-104">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="b28c0-105">Ancak, tek bir işlemde serisinde exchange sırasında başarısız olursa, tüm exchange başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b28c0-105">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="b28c0-106">Kitap alma ve kitaplığı, para almaz.</span><span class="sxs-lookup"><span data-stu-id="b28c0-106">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="b28c0-107">Exchange Dengeli ve öngörülebilir yapmaktan sorumlu teknolojisi, işlem adı verilir.</span><span class="sxs-lookup"><span data-stu-id="b28c0-107">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="b28c0-108">İşlemler işlem birimindeki tüm işlemleri başarıyla tamamlamak sürece veri yönelimli kaynakları kalıcı olarak güncelleştirilmez emin olun.</span><span class="sxs-lookup"><span data-stu-id="b28c0-108">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="b28c0-109">Tamamen başarılı ya da tamamen başarısız bir birim ilgili işlemlere kümesini birleştirerek hata kurtarma basitleştirmek ve uygulamanızı daha güvenilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b28c0-109">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="b28c0-110">Hareket işleme sistemleri bilgisayar donanımı ve yazılımı iş yürütmek gerekli rutin işlemleri gerçekleştirir işleme dayalı bir uygulamayı barındıran oluşur.</span><span class="sxs-lookup"><span data-stu-id="b28c0-110">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="b28c0-111">Örnekler yönetme sipariş girişi, uçak ayırmaları, bordro, üretim ve sevkiyat çalışan kayıtları, sistemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b28c0-111">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="b28c0-112">Bu bölüm hem işlem hakkında genel bilgiler ve işlemsel uygulamaları ve Microsoft .NET Framework kullanarak kaynak yöneticileri yazma konusunda belirli bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b28c0-112">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b28c0-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b28c0-113">In This Section</span></span>  
 [<span data-ttu-id="b28c0-114">İşlem temelleri</span><span class="sxs-lookup"><span data-stu-id="b28c0-114">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 <span data-ttu-id="b28c0-115">Temel işlem terimleri ve kavramları işleme tanıtır.</span><span class="sxs-lookup"><span data-stu-id="b28c0-115">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="b28c0-116">System.Transactions tarafından sağlanan özellikleri</span><span class="sxs-lookup"><span data-stu-id="b28c0-116">Features Provided by System.Transactions</span></span>](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 <span data-ttu-id="b28c0-117">Özellikleri System.Transactions işlem uygulamanızı yazmak için nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b28c0-117">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b28c0-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b28c0-118">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="b28c0-119">Kodunuzu işlemlere katılmasına izin sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b28c0-119">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="b28c0-120">Sınıfları birden fazla dağıtılmış katılımcıları, birden çok aşaması bildirimleri ve kalıcı kayıtlar ile işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b28c0-120">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
