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
# <a name="how-to-add-custom-data-to-ink-data"></a>Nasıl yapılır: Mürekkep Verisine Özel Veri Ekleme
Özel veri mürekkep mürekkep seri hale getirilmiş biçimi (ISF) olarak kaydedildiğinde, kaydedilecek mürekkep ekleyebilirsiniz.  Özel verileri kaydedebilirsiniz <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, veya <xref:System.Windows.Ink.Stroke>.  Özel verileri üç nesnelerde kaydetmek için verileri kaydetmek için en iyi yere karar olanağı sağlar.  Üç tüm sınıflar benzer yöntemler depolamak ve özel verilere erişmek için kullanır.  
  
 Özel verileri olarak yalnızca şu türleri kaydedilebilir:  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>[]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>[]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>[]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>[]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>[]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>[]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>[]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>[]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>[]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>[]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>[]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>[]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>[]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ekleme ve özel verilerin alınacağı gösterilmektedir bir <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 Aşağıdaki örnek, görüntüleyen bir uygulama oluşturur. bir <xref:System.Windows.Controls.InkCanvas> ve iki düğme.  Düğme `switchAuthor`, iki kalemin iki farklı yazar tarafından kullanılmasına izin verir.  Düğme `changePenColors` üzerindeki her vuruşun rengini değiştirir <xref:System.Windows.Controls.InkCanvas> göre yazar.  İki uygulama tanımlar <xref:System.Windows.Ink.DrawingAttributes> nesneleri ve hangi yazar u çizdiğini gösteren her biri için özel bir özellik ekler <xref:System.Windows.Ink.Stroke>.  Kullanıcı tıkladığında `changePenColors`, uygulama özel özellik değerini göre vuruşun görünümünü değiştirir.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
