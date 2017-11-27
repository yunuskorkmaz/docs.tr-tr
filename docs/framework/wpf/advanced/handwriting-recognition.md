---
title: "El Yazısı Tanıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8a202d4698c968a91a3d930138290cedfe3a83b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="handwriting-recognition"></a>El Yazısı Tanıma
WPF Platform dijital mürekkep ilgili olarak bu bölümde tanıma temelleri açıklanır.  
  
## <a name="recognition-solutions"></a>Tanıma çözümleri  
 Aşağıdaki örnek, mürekkep kullanarak tanımak gösterilmiştir [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) sınıfı.  
  
> [!NOTE]
>  Bu örnek yükseltirseniz sistemde yüklü olmasını gerektirir.  
  
 Adlı Visual Studio'da yeni bir WPF uygulaması projesi oluşturma **InkRecognition**. Window1.xaml dosyasının içeriğini aşağıdaki XAML kod ile değiştirin. Bu kod uygulamanın kullanıcı arabirimi işler.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 \Program Files\Microsoft Shared\Ink bulunabilir Microsoft.Ink.dll Microsoft Ink derlemesine başvuru ekleyin. Dosyanın arkasındaki kod içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
