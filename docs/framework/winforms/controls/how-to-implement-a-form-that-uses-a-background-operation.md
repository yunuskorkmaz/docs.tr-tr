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
ms.openlocfilehash: df7c6caf7b23824a596e94e1bd62205907b0b56a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592414"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="0498f-102">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="0498f-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="0498f-103">Aşağıdaki örnek program Fibonacci numaraları hesaplayan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0498f-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="0498f-104">Hesaplama kullanıcı arabirimi hesaplama devam ettikçe gecikmeler çalışmaya devam eder, kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="0498f-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="0498f-105">Visual Studio'da bu görevi için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="0498f-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="0498f-106">Ayrıca bkz: [izlenecek yol: Arka plan işlemi kullanan bir Form uygulama](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="0498f-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0498f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0498f-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0498f-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0498f-108">Compiling the Code</span></span>  
 <span data-ttu-id="0498f-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0498f-109">This example requires:</span></span>  
  
- <span data-ttu-id="0498f-110">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="0498f-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0498f-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0498f-111">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0498f-112">Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="0498f-112">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="0498f-113">Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="0498f-113">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0498f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0498f-114">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="0498f-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0498f-115">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="0498f-116">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0498f-116">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
