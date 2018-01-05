---
title: "Nasıl yapılır: Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme"
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
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a1292dae3a6fc7e86387ecbe3bf2b1da6912cc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme
Bu örnek, bir animasyon kullanmadan bir özelliğe uygulamak için bir yol gösterir. bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Bu işlevsellik kullanılamaz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. İçinde bir özelliğe animasyon ekleme hakkında bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Bir özellik için yerel bir animasyon uygulamak için kullanmak <xref:System.Windows.UIElement.BeginAnimation%2A> yöntemi. Bu yöntemi iki parametre alır: bir <xref:System.Windows.DependencyProperty> animasyon eklenecek özelliği ve bu özelliğe uygulanacak animasyon belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek genişlik ve arka plan rengi animasyon gösterilmektedir bir <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Animasyon sınıfları çeşitli <xref:System.Windows.Media.Animation> ad alanı mevcut özellikler farklı türde animasyon için. Özellikleri hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Bağımlılık özellikleri (Bu örneklerde gösterilen özellikleri türü) ve bunların özellikleri hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Diğer yolu kullanmadan animasyon <xref:System.Windows.Media.Animation.Storyboard> nesneleri; daha fazla bilgi için bkz [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
