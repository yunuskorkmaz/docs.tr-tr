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
ms.openlocfilehash: 03ffec87c98c88452aa8fde89c64646eaf48a8da
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369597"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği için Sahip Türü Ekleme
Bu örnekte, farklı bir tür için kayıtlı bir bağımlılık özelliği sahibi olarak bir sınıf eklemek gösterilmektedir. Bunu yaparak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu ve özellik sistemi olan her ikisi de ek bir özellik sahibi olarak sınıf tanıyabilir. Sahibi olarak isteğe bağlı olarak ekleme, türe özgü meta verilerini sağlamak ekleme sınıfına olanak tanır.  
  
 Aşağıdaki örnekte, `StateProperty` bir özellik tarafından kaydedilen `MyStateControl` sınıfı. Sınıf `UnrelatedStateControl` kendisini sahiplerinden biri ekler `StateProperty` kullanarak <xref:System.Windows.DependencyProperty.AddOwner%2A> yöntemi, özellikle ekleme türü üzerinde var olduğundan, bağımlılık özelliği için yeni meta veriler sağlayan imza kullanılıyor. Sağlamalısınız dikkat edin [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] gösterilen örneğe benzer bir özellik için erişimciler [bağımlılık özelliği uygulama](how-to-implement-a-dependency-property.md) örnek yanı sıra yeniden eklenen sınıf bağımlılık özelliği tanımlayıcıyı kullanıma sunar. sahibi olarak.  
  
 Sarmalayıcılar olmadan, bağımlılık özelliği hala programlı erişim kullanmanın açısından işe yarar <xref:System.Windows.DependencyObject.GetValue%2A> veya <xref:System.Windows.DependencyObject.SetValue%2A>. Ancak, genellikle bu özelliği sistem davranışı ile paralel istediğiniz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği sarmalayıcıları. Sarmalayıcılar, bağımlılık özelliği program üzerinden ayarlamak daha kolay hale getirmek ve özellikleri olarak ayarlanacak mümkün kılar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri.  
  
 Varsayılan meta verileri geçersiz kılma konusunda bilgi edinmek için bkz: [bağımlılık özelliği meta verileri geçersiz kılma](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
