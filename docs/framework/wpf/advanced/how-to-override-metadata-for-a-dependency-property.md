---
title: 'Nasıl yapılır: Bağımlılık Özelliği için Meta Verileri Geçersiz Kılma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
ms.openlocfilehash: 5d2d692984bef34569b2c4bb80c3fb072e4c3f79
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365886"
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği için Meta Verileri Geçersiz Kılma
Bu örnek, devralınan bir sınıftan çağırarak gelen varsayılan bağımlılık özelliği meta verileri geçersiz kılma işlemi gösterilmektedir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemi ve türe özgü meta veriler sağlar.  
  
## <a name="example"></a>Örnek  
 Tanımlayarak kendi <xref:System.Windows.PropertyMetadata>, bir sınıf kendi varsayılan değeri ve özellik sistemi geri aramaları gibi bağımlılık özelliği davranışları tanımlayabilirsiniz. Birçok bağımlılık özelliği sınıfları, kullanıcıların kayıt işleminin bir parçası oluşturulan varsayılan meta verileri zaten var. Bu parçası olan bağımlılık özelliklerini içeren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Bağımlılık özelliği, sınıf devralma yoluyla devralınan bir sınıf, meta veriler üzerinden değiştirilebilir özelliği özelliklerini herhangi bir alt sınıf özgü gereksinimler eşleşir, böylece özgün metaverileri gereğince geçersiz kılabilirsiniz.  
  
 Bağımlılık özelliği meta verileri geçersiz kılma kullanın (Bu özelliği kaydetme nesnelerin belirli örneklerini örneği saati karşılık gelir) özellik sistemi tarafından yerleştirilen bu özelliği önce yapılmalıdır. Çağrılar <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> olarak kendisini sağlayan bir tür statik oluşturucuları içinde gerçekleştirilmelidir `forType` parametresinin <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Sahip türünün örneği varolduğunda meta verileri değiştirmeye çalışırsanız, bu özel durumları oluşturmaz, ancak özellik sistemindeki tutarsız davranışlara neden olur. Ayrıca, meta veriler yalnızca bir kez başına türü geçersiz kılınabilir. Sonraki denemeler aynı tür meta verileri geçersiz kılma için bir özel durum oluşturacak.  
  
 Aşağıdaki örnekte, özel bir sınıf `MyAdvancedStateControl` için sağlanan meta verileri geçersiz kılar `StateProperty` tarafından `MyAdvancedStateControl` ile yeni özellik meta verileri. Örneği için varsayılan değeri `StateProperty` artık `true` özelliği sorgulanan zaman yeni oluşturulmuş üzerinde `MyAdvancedStateControl` örneği.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Nasıl Yapılır Konuları](properties-how-to-topics.md)
