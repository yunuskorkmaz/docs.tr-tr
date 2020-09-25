---
title: İşlem Gerçekleştirme
description: .NET 'te işlem işlemeyi gözden geçirin. İşlemler, tüm işlemler başarıyla tamamlanmadığı takdirde veri odaklı kaynakların kalıcı olarak güncelleştirilmesini sağlamaktır.
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: bbf2448128da7df8af415ff5dea7e3cd8af24d1e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186815"
---
# <a name="transaction-processing"></a><span data-ttu-id="0520d-104">İşlem Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="0520d-104">Transaction Processing</span></span>

<span data-ttu-id="0520d-105">Bir çevrimiçi bir kitaplığı defterinden satın aldığınızda, bir kitap (kredi biçiminde) karşılığında exchange.</span><span class="sxs-lookup"><span data-stu-id="0520d-105">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="0520d-106">Kredi iyi ise, bir dizi ilgili operations defteri alma ve kitaplığı, para alır sağlar.</span><span class="sxs-lookup"><span data-stu-id="0520d-106">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="0520d-107">Ancak, tek bir işlemde serisinde exchange sırasında başarısız olursa, tüm exchange başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0520d-107">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="0520d-108">Kitap alma ve kitaplığı, para almaz.</span><span class="sxs-lookup"><span data-stu-id="0520d-108">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="0520d-109">Exchange dengeli ve öngörülebilir hale getirmekten sorumlu teknoloji işlem işleme olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0520d-109">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="0520d-110">İşlemler, işlem birimi içindeki tüm işlemler başarıyla tamamlanmadığı takdirde veri odaklı kaynakların kalıcı olarak güncelleştirilmesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="0520d-110">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="0520d-111">Tamamen başarılı ya da tamamen başarısız bir birim ilgili işlemlere kümesini birleştirerek hata kurtarma basitleştirmek ve uygulamanızı daha güvenilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0520d-111">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="0520d-112">İşlem işleme sistemleri, iş yürütmek için gereken rutin işlemleri gerçekleştiren bir işlem odaklı uygulamayı barındıran bilgisayar donanımlarından ve yazılımından oluşur.</span><span class="sxs-lookup"><span data-stu-id="0520d-112">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="0520d-113">Örnek olarak, satış siparişi girişi, hava yolu ayırmaları, bordro, çalışan kayıtları, üretim ve Sevkiyat yönetimi gibi sistemler bulunur.</span><span class="sxs-lookup"><span data-stu-id="0520d-113">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="0520d-114">Bu bölüm, işlem işleme hakkında genel bilgi ve Microsoft .NET çerçevesini kullanarak işlem uygulamalarının ve kaynak yöneticilerinin nasıl yazılacağı hakkında belirli bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0520d-114">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0520d-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0520d-115">In This Section</span></span>  

 [<span data-ttu-id="0520d-116">İşlem Temelleri</span><span class="sxs-lookup"><span data-stu-id="0520d-116">Transaction Fundamentals</span></span>](transaction-fundamentals.md)  
 <span data-ttu-id="0520d-117">Temel işlem işleme hüküm ve kavramlarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="0520d-117">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="0520d-118">System.Transactions Tarafından Sağlanan Özellikler</span><span class="sxs-lookup"><span data-stu-id="0520d-118">Features Provided by System.Transactions</span></span>](features-provided-by-system-transactions.md)  
 <span data-ttu-id="0520d-119">Kendi işlem uygulamanızı yazmak için System. Transactions içindeki özellikleri nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="0520d-119">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0520d-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="0520d-120">Reference</span></span>  

 <xref:System.Transactions>  
 <span data-ttu-id="0520d-121">Kodunuzun işlemlere katılmasına izin veren sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0520d-121">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="0520d-122">Sınıflar birden çok dağıtılmış katılımcı, birden çok aşama bildirimi ve kalıcı kayıtlar içeren işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="0520d-122">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
