---
title: 'Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama'
description: Başka bir işlem devam ederken bir işlemin çalışmaya devam edebilmesi için bir arka plan işlemi kullanan bir Windows formu uygulamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 23bf4bc02fbf998d92dfce6d84e4e337cbefe7d9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174529"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="fee4a-103">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="fee4a-103">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="fee4a-104">Aşağıdaki örnek program Fibonaccı numaralarını hesaplayan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fee4a-104">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="fee4a-105">Hesaplama, Kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır, bu nedenle hesaplama ilerledikçe Kullanıcı arabirimi gecikmeler olmadan çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="fee4a-105">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="fee4a-106">Visual Studio 'da bu görev için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="fee4a-106">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="fee4a-107">Ayrıca bkz. [Izlenecek yol: arka plan Işlemi kullanan bir form uygulama](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="fee4a-107">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fee4a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="fee4a-108">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fee4a-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fee4a-109">Compiling the Code</span></span>  
 <span data-ttu-id="fee4a-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fee4a-110">This example requires:</span></span>  
  
- <span data-ttu-id="fee4a-111">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="fee4a-111">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fee4a-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fee4a-112">Robust Programming</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="fee4a-113">Herhangi bir sıralamanın çoklu iş parçacığı kullanımı kullanılırken, kendinizi çok önemli ve karmaşık hatalara maruz kalırsınız.</span><span class="sxs-lookup"><span data-stu-id="fee4a-113">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="fee4a-114">Çoklu iş parçacığı kullanan herhangi bir çözümü uygulamadan önce, [yönetilen Iş parçacığı En Iyi uygulamalarına](../../../standard/threading/managed-threading-best-practices.md) danışın.</span><span class="sxs-lookup"><span data-stu-id="fee4a-114">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee4a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fee4a-115">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="fee4a-116">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fee4a-116">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="fee4a-117">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="fee4a-117">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
