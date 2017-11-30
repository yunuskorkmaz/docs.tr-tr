---
title: "Nasıl yapılır: Bağımlılık Özelliği için Sahip Türü Ekleme"
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
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 079f08e1c330b710748ea6bb1aab8ccfb7ae7016
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği için Sahip Türü Ekleme
Bu örnekte, farklı bir tür için kayıtlı bir bağımlılık özelliğinin sahibi olarak bir sınıf eklemek gösterilmiştir. Bunu yaparak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu ve özellik sisteminin olan her ikisi de ek bir özellik sahibi olarak sınıfı tanıyabilir. Sahibi olarak isteğe bağlı olarak ekleme, türe özgü meta verilerini sağlamak ekleme sınıfına olanak tanır.  
  
 Aşağıdaki örnekte, `StateProperty` bir özellik tarafından kayıtlı `MyStateControl` sınıfı. Sınıf `UnrelatedStateControl` kendisini sahibi olarak ekler `StateProperty` kullanarak <xref:System.Windows.DependencyProperty.AddOwner%2A> yöntemi, özellikle ekleme türü üzerinde mevcut olmadığından, bağımlılık özelliği için yeni meta sağlayan imza kullanarak. Sağlamaları gereken bildirim [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] erişimciler gösterilen örneğe benzer bir özellik için [bağımlılık özelliği uygulama](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) örnek olarak eklenen sınıf üzerinde bağımlılık özelliği tanımlayıcısını'yeniden kullanıma sahibi olarak.  
  
 Sarmalayıcılar olmadan bağımlılık özelliği hala programlı erişim kullanmanın açısından çalışır <xref:System.Windows.DependencyObject.GetValue%2A> veya <xref:System.Windows.DependencyObject.SetValue%2A>. Ancak, genellikle bu özelliği sistem davranışı ile paralel istediğiniz [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği sarmalayıcıları. Sarmalayıcılar bağımlılık özelliği programlı olarak ayarlamak kolaylaştırmak ve özellikleri olarak ayarlamayı olanaklı hale getirir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri.  
  
 Varsayılan meta verileri geçersiz kılmak nasıl öğrenmek için bkz: [bağımlılık özelliği için geçersiz meta veriler](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
