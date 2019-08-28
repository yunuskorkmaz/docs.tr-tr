---
title: 'Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama'
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
ms.openlocfilehash: e06b18558f6b3fa3cef47613bbaef16fb7c740f0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046200"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="40d9b-102">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="40d9b-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="40d9b-103">Aşağıdaki örnek program Fibonaccı numaralarını hesaplayan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40d9b-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="40d9b-104">Hesaplama, Kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır, bu nedenle hesaplama ilerledikçe Kullanıcı arabirimi gecikmeler olmadan çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="40d9b-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="40d9b-105">Visual Studio 'da bu görev için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="40d9b-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="40d9b-106">Ayrıca bkz [. İzlenecek yol: Arka plan Işlemi](walkthrough-implementing-a-form-that-uses-a-background-operation.md)kullanan bir form uygulama.</span><span class="sxs-lookup"><span data-stu-id="40d9b-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40d9b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="40d9b-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40d9b-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="40d9b-108">Compiling the Code</span></span>  
 <span data-ttu-id="40d9b-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="40d9b-109">This example requires:</span></span>  
  
- <span data-ttu-id="40d9b-110">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="40d9b-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="40d9b-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="40d9b-111">Robust Programming</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="40d9b-112">Herhangi bir sıralamanın çoklu iş parçacığı kullanımı kullanılırken, kendinizi çok önemli ve karmaşık hatalara maruz kalırsınız.</span><span class="sxs-lookup"><span data-stu-id="40d9b-112">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="40d9b-113">Çoklu iş parçacığı kullanan herhangi bir çözümü uygulamadan önce, [yönetilen Iş parçacığı En Iyi uygulamalarına](../../../standard/threading/managed-threading-best-practices.md) danışın.</span><span class="sxs-lookup"><span data-stu-id="40d9b-113">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d9b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40d9b-114">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="40d9b-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="40d9b-115">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="40d9b-116">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="40d9b-116">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
