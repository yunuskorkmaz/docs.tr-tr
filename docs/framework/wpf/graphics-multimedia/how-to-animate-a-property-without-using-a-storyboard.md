---
title: 'Nasıl yapılır: Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963019"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme
Bu örnek, bir özelliğini kullanmadan bir özelliği bir <xref:System.Windows.Media.Animation.Storyboard>animasyon uygulamak için bir yol gösterir.  
  
> [!NOTE]
> Bu işlev ' de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]kullanılamaz. İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir özelliği hareketlendirme hakkında daha fazla bilgi için bkz. [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Bir özelliğe yerel animasyon uygulamak için <xref:System.Windows.UIElement.BeginAnimation%2A> yöntemini kullanın. Bu yöntem iki parametre alır: bir <xref:System.Windows.DependencyProperty> animasyon uygulanacak özelliği belirten ve bu özelliğe uygulanacak animasyon.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesinin <xref:System.Windows.Controls.Button>genişlik ve arka plan rengine nasıl animasyon ekleneceğini gösterir.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Farklı özellik türlerini hareketlendirmek için <xref:System.Windows.Media.Animation> ad alanındaki çeşitli animasyon sınıfları mevcuttur. Hareketlendirilen özellikler hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md). Bağımlılık özellikleri (Bu örneklerde gösterilen özelliklerin türü) ve özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md).  
  
 Nesneleri kullanmadan <xref:System.Windows.Media.Animation.Storyboard> hareketlendirmek için başka yollar vardır; daha fazla bilgi için bkz. [özellik animasyon tekniklerine genel bakış](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
