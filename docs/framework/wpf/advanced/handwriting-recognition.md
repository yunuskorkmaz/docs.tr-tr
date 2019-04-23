---
title: El Yazısı Tanıma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: 417af272514ac9ce68c8faa72339f2befc2dd7c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170202"
---
# <a name="handwriting-recognition"></a><span data-ttu-id="4736a-102">El Yazısı Tanıma</span><span class="sxs-lookup"><span data-stu-id="4736a-102">Handwriting Recognition</span></span>
<span data-ttu-id="4736a-103">Dijital Mürekkep WPF platformu ile ilgili olarak bu bölümde tanıma temelleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4736a-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="4736a-104">Tanıma çözümleri</span><span class="sxs-lookup"><span data-stu-id="4736a-104">Recognition Solutions</span></span>  
 <span data-ttu-id="4736a-105">Aşağıdaki örnek mürekkep kullanarak anlamayı gösterir [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4736a-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4736a-106">Bu örnek, yükseltirseniz sistemde yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4736a-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="4736a-107">Visual Studio adlı yeni bir WPF uygulaması projesi oluşturma **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="4736a-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="4736a-108">Gt;Window1.xaml dosyasının içeriğini aşağıdaki XAML kod ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4736a-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="4736a-109">Bu kod, uygulamanın kullanıcı arabirimini işler.</span><span class="sxs-lookup"><span data-stu-id="4736a-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="4736a-110">\Program Files\Microsoft Shared\Ink içinde bulunan Microsoft.Ink.dll Microsoft Ink derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4736a-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="4736a-111">Arka plan kod dosyasında içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4736a-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4736a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4736a-112">See also</span></span>

- <span data-ttu-id="4736a-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4736a-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span></span>
