---
title: 'Nasıl yapılır: Bağımlılık Özelliği Uygulama'
description: Bir DependencyProperty alanı ile ortak dil çalışma zamanı özelliğini yedekleyerek Windows Presentation Foundation ' de bir bağımlılık özelliği tanımlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 673f653a9b02627efcccdfe08c4812ca0834217c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165089"
---
# <a name="how-to-implement-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği Uygulama
Bu örnek, bir ortak dil çalışma zamanı (CLR) özelliğinin bir alanla nasıl geri alınacağını gösterir <xref:System.Windows.DependencyProperty> ve bu nedenle bir bağımlılık özelliği tanımlar. Kendi özelliklerinizi tanımladığınızda ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Stiller, veri bağlama, devralma, animasyon ve varsayılan değerler dahil olmak üzere işlevlerin birçok yönlerini desteklemek istiyorsanız, bunları bir bağımlılık özelliği olarak uygulamalısınız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek öncelikle yöntemini çağırarak bir bağımlılık özelliği kaydeder <xref:System.Windows.DependencyProperty.Register%2A> . Dependency özelliğinin adını ve özelliklerini depolamak için kullandığınız tanımlayıcı alanının adı, <xref:System.Windows.DependencyProperty.Name%2A> çağrının bir parçası olarak <xref:System.Windows.DependencyProperty.Register%2A> , değişmez dize tarafından eklenen bağımlılık özelliği için seçtiğiniz olmalıdır `Property` . Örneğin, ' a bir bağımlılık özelliği kaydettiğinizde <xref:System.Windows.DependencyProperty.Name%2A> `Location` , bağımlılık özelliği için tanımladığınız tanımlayıcı alanın adı olmalıdır `LocationProperty` .  
  
 Bu örnekte, Dependency özelliğinin adı ve CLR erişimcisi ' dir `State` ; tanımlayıcı alanı, `StateProperty` özelliğin türü <xref:System.Boolean> ve bağımlılık özelliğini kaydeden tür olur `MyStateControl` .  
  
 Bu adlandırma modelini izlemeden, tasarımcılar özelliği doğru şekilde bildiremeyebilir ve özellik sistem stili uygulamasının belirli yönleri beklendiği gibi davranmayabilir.  
  
 Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz. Bu örnek, bağımlılık özelliğinin varsayılan değerini olarak kaydeder `State` `false` .  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Bir bağımlılık özelliğinin nasıl ve neden uygulanacağı hakkında daha fazla bilgi için, yalnızca bir CLR özelliğinin özel bir alanla yedeklenmesinin aksine, bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Nasıl Yapılır Konuları](properties-how-to-topics.md)
