---
title: 'Nasıl yapılır: Bağımlılık Özelliği için Sahip Türü Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401124"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği için Sahip Türü Ekleme
Bu örnek, farklı bir tür için kaydedilen Dependency özelliğinin sahibi olarak bir sınıfın nasıl ekleneceğini gösterir. Bunu yaptığınızda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu ve özellik sistemi, özelliğin ek sahibi olarak sınıfını tanıyabilecektir. Sahip olarak eklemek, isteğe bağlı olarak türe özgü meta veriler sağlamak için sınıfın eklenmesine izin verir.  
  
 Aşağıdaki örnekte, `StateProperty` `MyStateControl` sınıfı tarafından kaydedilen bir özelliktir. Sınıfı `UnrelatedStateControl` , özellikle, ekleme türü üzerinde olduğu gibi `StateProperty` bağımlılık özelliği için yeni meta verilere izin veren imzayı kullanarak kendisini kullanarak <xref:System.Windows.DependencyProperty.AddOwner%2A> kendi sahibi olarak ekler. Özellik için ortak dil çalışma zamanı (CLR) erişimcileri sağlamanız gerektiğine dikkat edin. bunun yanı sıra, sahip olarak eklenmekte [](how-to-implement-a-dependency-property.md) olan sınıfta bağımlılık özellik tanımlayıcısını yeniden kullanıma sunar.  
  
 Sarmalayıcılar olmadan, bağımlılık özelliği, veya <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>kullanılarak programlı erişim perspektifinden çalışmaya devam eder. Ancak, bu özellik sistem davranışının CLR özellik sarmalayıcılarıyla paralel olmasını sağlar. Sarmalayıcılar, bağımlılık özelliğini programlı bir şekilde ayarlamayı kolaylaştırır ve özellikleri öznitelik olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayarlamayı mümkün hale getirir.  
  
 Varsayılan meta verileri nasıl geçersiz kılabileceğinizi öğrenmek için bkz. [bir bağımlılık özelliği Için meta verileri geçersiz kılma](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
