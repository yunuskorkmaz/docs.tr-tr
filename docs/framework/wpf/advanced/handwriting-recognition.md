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
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956526"
---
# <a name="handwriting-recognition"></a><span data-ttu-id="77991-102">El Yazısı Tanıma</span><span class="sxs-lookup"><span data-stu-id="77991-102">Handwriting Recognition</span></span>
<span data-ttu-id="77991-103">Bu bölümde, WPF platformunda dijital mürekkeple ilgili olarak tanımanın temelleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77991-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="77991-104">Tanıma çözümleri</span><span class="sxs-lookup"><span data-stu-id="77991-104">Recognition Solutions</span></span>  
 <span data-ttu-id="77991-105">Aşağıdaki örnek, [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) sınıfını kullanarak mürekkebin nasıl tanınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="77991-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77991-106">Bu örnek, el yazısı tanıyıcılarının sistemde yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="77991-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="77991-107">Visual Studio 'da **ınktanıması**adlı yenı bir WPF uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="77991-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="77991-108">Window1. xaml dosyasının içeriğini aşağıdaki XAML kodu ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="77991-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="77991-109">Bu kod, uygulamanın kullanıcı arabirimini işler.</span><span class="sxs-lookup"><span data-stu-id="77991-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="77991-110">\Program Files\Common Files\Microsoft Shared\ınk' te bulunan Microsoft Ink derlemesine (Microsoft. Ink. dll) bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77991-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="77991-111">Arka plan kod dosyasının içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="77991-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="77991-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77991-112">See also</span></span>

- <span data-ttu-id="77991-113">[Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="77991-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span></span>
