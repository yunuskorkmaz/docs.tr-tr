---
title: "Nasıl yapılır: Mürekkep Verisine Özel Veri Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f266f3c98ca64c80ccbb669a1cc646321754579f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="0f2c6-102">Nasıl yapılır: Mürekkep Verisine Özel Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="0f2c6-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="0f2c6-103">Özel veri mürekkep mürekkep seri hale getirilmiş biçimi (ISF) olarak kaydedildiğinde, kaydedilecek mürekkep ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="0f2c6-104">Özel verileri kaydedebilirsiniz <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, veya <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="0f2c6-105">Özel verileri üç nesnelerde kaydetmek için verileri kaydetmek için en iyi yere karar olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="0f2c6-106">Üç tüm sınıflar benzer yöntemler depolamak ve özel verilere erişmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="0f2c6-107">Özel verileri olarak yalnızca şu türleri kaydedilebilir:</span><span class="sxs-lookup"><span data-stu-id="0f2c6-107">Only the following types can be saved as custom data:</span></span>  
  
-   <xref:System.Boolean>  
  
-   <span data-ttu-id="0f2c6-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-108"><xref:System.Boolean>[]</span></span>  
  
-   <xref:System.Byte>  
  
-   <span data-ttu-id="0f2c6-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-109"><xref:System.Byte>[]</span></span>  
  
-   <xref:System.Char>  
  
-   <span data-ttu-id="0f2c6-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-110"><xref:System.Char>[]</span></span>  
  
-   <xref:System.DateTime>  
  
-   <span data-ttu-id="0f2c6-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-111"><xref:System.DateTime>[]</span></span>  
  
-   <xref:System.Decimal>  
  
-   <span data-ttu-id="0f2c6-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-112"><xref:System.Decimal>[]</span></span>  
  
-   <xref:System.Double>  
  
-   <span data-ttu-id="0f2c6-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-113"><xref:System.Double>[]</span></span>  
  
-   <xref:System.Int16>  
  
-   <span data-ttu-id="0f2c6-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-114"><xref:System.Int16>[]</span></span>  
  
-   <xref:System.Int32>  
  
-   <span data-ttu-id="0f2c6-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-115"><xref:System.Int32>[]</span></span>  
  
-   <xref:System.Int64>  
  
-   <span data-ttu-id="0f2c6-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-116"><xref:System.Int64>[]</span></span>  
  
-   <xref:System.Single>  
  
-   <span data-ttu-id="0f2c6-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-117"><xref:System.Single>[]</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <span data-ttu-id="0f2c6-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-118"><xref:System.UInt16>[]</span></span>  
  
-   <xref:System.UInt32>  
  
-   <span data-ttu-id="0f2c6-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-119"><xref:System.UInt32>[]</span></span>  
  
-   <xref:System.UInt64>  
  
-   <span data-ttu-id="0f2c6-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="0f2c6-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f2c6-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f2c6-121">Example</span></span>  
 <span data-ttu-id="0f2c6-122">Aşağıdaki örnek ekleme ve özel verilerin alınacağı gösterilmektedir bir <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="0f2c6-123">Aşağıdaki örnek, görüntüleyen bir uygulama oluşturur. bir <xref:System.Windows.Controls.InkCanvas> ve iki düğme.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="0f2c6-124">Düğme `switchAuthor`, iki kalemin iki farklı yazar tarafından kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="0f2c6-125">Düğme `changePenColors` üzerindeki her vuruşun rengini değiştirir <xref:System.Windows.Controls.InkCanvas> göre yazar.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="0f2c6-126">İki uygulama tanımlar <xref:System.Windows.Ink.DrawingAttributes> nesneleri ve hangi yazar u çizdiğini gösteren her biri için özel bir özellik ekler <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="0f2c6-127">Kullanıcı tıkladığında `changePenColors`, uygulama özel özellik değerini göre vuruşun görünümünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0f2c6-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
