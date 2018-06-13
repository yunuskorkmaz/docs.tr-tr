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
ms.openlocfilehash: d72d8b42a23205d8599b23a467677dd2f05d5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542382"
---
# <a name="handwriting-recognition"></a><span data-ttu-id="a1165-102">El Yazısı Tanıma</span><span class="sxs-lookup"><span data-stu-id="a1165-102">Handwriting Recognition</span></span>
<span data-ttu-id="a1165-103">WPF Platform dijital mürekkep ilgili olarak bu bölümde tanıma temelleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a1165-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="a1165-104">Tanıma çözümleri</span><span class="sxs-lookup"><span data-stu-id="a1165-104">Recognition Solutions</span></span>  
 <span data-ttu-id="a1165-105">Aşağıdaki örnek, mürekkep kullanarak tanımak gösterilmiştir [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a1165-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1165-106">Bu örnek yükseltirseniz sistemde yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1165-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="a1165-107">Adlı Visual Studio'da yeni bir WPF uygulaması projesi oluşturma **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="a1165-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="a1165-108">Window1.xaml dosyasının içeriğini aşağıdaki XAML kod ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a1165-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="a1165-109">Bu kod uygulamanın kullanıcı arabirimi işler.</span><span class="sxs-lookup"><span data-stu-id="a1165-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a1165-110">\Program Files\Microsoft Shared\Ink bulunabilir Microsoft.Ink.dll Microsoft Ink derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1165-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="a1165-111">Dosyanın arkasındaki kod içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a1165-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a1165-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1165-112">See Also</span></span>  
 <span data-ttu-id="a1165-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a1165-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
