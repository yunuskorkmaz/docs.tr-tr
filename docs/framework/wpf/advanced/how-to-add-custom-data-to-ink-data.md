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
# <a name="how-to-add-custom-data-to-ink-data"></a>Nasıl yapılır: Mürekkep Verisine Özel Veri Ekleme
Mürekkep mürekkep seri hale getirilmiş biçimi (ISF) kaydedildiğinde, kaydedilecek mürekkep özel veri ekleyebilirsiniz.  Özel verileri kaydedebilirsiniz <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, veya <xref:System.Windows.Ink.Stroke>.  Üç nesneler üzerinde özel veri kaydedebilme verileri kaydetmek için en iyi yeri karar verme olanağı sağlar.  Üç özel verilere erişmek ve depolamak için benzer yöntemler kullanın.  
  
 Özel verileri olarak yalnızca şu türleri kaydedilebilir:  
  
- <xref:System.Boolean>  
  
- <xref:System.Boolean>[]  
  
- <xref:System.Byte>  
  
- <xref:System.Byte>[]  
  
- <xref:System.Char>  
  
- <xref:System.Char>[]  
  
- <xref:System.DateTime>  
  
- <xref:System.DateTime>[]  
  
- <xref:System.Decimal>  
  
- <xref:System.Decimal>[]  
  
- <xref:System.Double>  
  
- <xref:System.Double>[]  
  
- <xref:System.Int16>  
  
- <xref:System.Int16>[]  
  
- <xref:System.Int32>  
  
- <xref:System.Int32>[]  
  
- <xref:System.Int64>  
  
- <xref:System.Int64>[]  
  
- <xref:System.Single>  
  
- <xref:System.Single>[]  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <xref:System.UInt16>[]  
  
- <xref:System.UInt32>  
  
- <xref:System.UInt32>[]  
  
- <xref:System.UInt64>  
  
- <xref:System.UInt64>[]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ekleme ve özel verilerin alınacağı gösterilmiştir bir <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 Aşağıdaki örnek, görüntüleyen bir uygulama oluşturur. bir <xref:System.Windows.Controls.InkCanvas> ve iki düğme.  Düğme `switchAuthor`, iki farklı yazar tarafından kullanılmak üzere iki kalemler sağlar.  Düğme `changePenColors` her vuruş rengi değiştirir <xref:System.Windows.Controls.InkCanvas> göre yazar.  İki uygulama tanımlar <xref:System.Windows.Ink.DrawingAttributes> nesneleri ve hangi yazar u çizdiğini gösteren her biri için özel bir özellik ekler <xref:System.Windows.Ink.Stroke>.  Kullanıcı tıkladığında `changePenColors`, uygulama özel özellik değerini göre stroke'un görünümü değiştirir.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
