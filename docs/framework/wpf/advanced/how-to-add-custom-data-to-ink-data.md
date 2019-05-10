---
title: 'Nasıl yapılır: Mürekkep Verisine Özel Veri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: 7c59a205df5358daec101339cc6a308c8e38a9d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640863"
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="51d4c-102">Nasıl yapılır: Mürekkep Verisine Özel Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="51d4c-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="51d4c-103">Mürekkep mürekkep seri hale getirilmiş biçimi (ISF) kaydedildiğinde, kaydedilecek mürekkep özel veri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51d4c-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="51d4c-104">Özel verileri kaydedebilirsiniz <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, veya <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="51d4c-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="51d4c-105">Üç nesneler üzerinde özel veri kaydedebilme verileri kaydetmek için en iyi yeri karar verme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="51d4c-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="51d4c-106">Üç özel verilere erişmek ve depolamak için benzer yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="51d4c-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="51d4c-107">Özel verileri olarak yalnızca şu türleri kaydedilebilir:</span><span class="sxs-lookup"><span data-stu-id="51d4c-107">Only the following types can be saved as custom data:</span></span>  
  
- <xref:System.Boolean>  
  
- <span data-ttu-id="51d4c-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-108"><xref:System.Boolean>[]</span></span>  
  
- <xref:System.Byte>  
  
- <span data-ttu-id="51d4c-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-109"><xref:System.Byte>[]</span></span>  
  
- <xref:System.Char>  
  
- <span data-ttu-id="51d4c-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-110"><xref:System.Char>[]</span></span>  
  
- <xref:System.DateTime>  
  
- <span data-ttu-id="51d4c-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-111"><xref:System.DateTime>[]</span></span>  
  
- <xref:System.Decimal>  
  
- <span data-ttu-id="51d4c-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-112"><xref:System.Decimal>[]</span></span>  
  
- <xref:System.Double>  
  
- <span data-ttu-id="51d4c-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-113"><xref:System.Double>[]</span></span>  
  
- <xref:System.Int16>  
  
- <span data-ttu-id="51d4c-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-114"><xref:System.Int16>[]</span></span>  
  
- <xref:System.Int32>  
  
- <span data-ttu-id="51d4c-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-115"><xref:System.Int32>[]</span></span>  
  
- <xref:System.Int64>  
  
- <span data-ttu-id="51d4c-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-116"><xref:System.Int64>[]</span></span>  
  
- <xref:System.Single>  
  
- <span data-ttu-id="51d4c-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-117"><xref:System.Single>[]</span></span>  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <span data-ttu-id="51d4c-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-118"><xref:System.UInt16>[]</span></span>  
  
- <xref:System.UInt32>  
  
- <span data-ttu-id="51d4c-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-119"><xref:System.UInt32>[]</span></span>  
  
- <xref:System.UInt64>  
  
- <span data-ttu-id="51d4c-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="51d4c-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="51d4c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="51d4c-121">Example</span></span>  
 <span data-ttu-id="51d4c-122">Aşağıdaki örnek, ekleme ve özel verilerin alınacağı gösterilmiştir bir <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="51d4c-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="51d4c-123">Aşağıdaki örnek, görüntüleyen bir uygulama oluşturur. bir <xref:System.Windows.Controls.InkCanvas> ve iki düğme.</span><span class="sxs-lookup"><span data-stu-id="51d4c-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="51d4c-124">Düğme `switchAuthor`, iki farklı yazar tarafından kullanılmak üzere iki kalemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="51d4c-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="51d4c-125">Düğme `changePenColors` her vuruş rengi değiştirir <xref:System.Windows.Controls.InkCanvas> göre yazar.</span><span class="sxs-lookup"><span data-stu-id="51d4c-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="51d4c-126">İki uygulama tanımlar <xref:System.Windows.Ink.DrawingAttributes> nesneleri ve hangi yazar u çizdiğini gösteren her biri için özel bir özellik ekler <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="51d4c-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="51d4c-127">Kullanıcı tıkladığında `changePenColors`, uygulama özel özellik değerini göre stroke'un görünümü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="51d4c-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
