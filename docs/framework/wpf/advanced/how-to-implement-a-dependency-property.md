---
title: 'Nasıl yapılır: Bağımlılık Özelliği Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400361"
---
# <a name="how-to-implement-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği Uygulama
Bu örnek, bir ortak dil çalışma zamanı (CLR) özelliğinin bir <xref:System.Windows.DependencyProperty> alanla nasıl geri alınacağını gösterir ve bu nedenle bir bağımlılık özelliği tanımlar. Kendi özelliklerinizi tanımladığınızda ve stiller, veri bağlama, devralma, animasyon ve varsayılan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] değerler dahil olmak üzere işlevlerin birçok yönlerini desteklemek istiyorsanız, bunları bir bağımlılık özelliği olarak uygulamalısınız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek öncelikle <xref:System.Windows.DependencyProperty.Register%2A> yöntemini çağırarak bir bağımlılık özelliği kaydeder. Dependency özelliğinin adını ve özelliklerini depolamak için kullandığınız tanımlayıcı alanının adı, <xref:System.Windows.DependencyProperty.Name%2A> <xref:System.Windows.DependencyProperty.Register%2A> çağrının bir parçası olarak, değişmez dize `Property`tarafından eklenen bağımlılık özelliği için seçtiğiniz olmalıdır. Örneğin, ' a bir <xref:System.Windows.DependencyProperty.Name%2A> `Location`bağımlılık özelliği kaydettiğinizde, bağımlılık özelliği için tanımladığınız tanımlayıcı alanın adı `LocationProperty`olmalıdır.  
  
 Bu örnekte, Dependency özelliğinin `State`adı ve clr erişimcisi ' dir; tanımlayıcı alanı, `StateProperty`özelliğin <xref:System.Boolean>türü ve bağımlılık özelliğini `MyStateControl`kaydeden tür olur.  
  
 Bu adlandırma modelini izlemeden, tasarımcılar özelliği doğru şekilde bildiremeyebilir ve özellik sistem stili uygulamasının belirli yönleri beklendiği gibi davranmayabilir.  
  
 Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz. Bu örnek, `State` bağımlılık özelliğinin `false`varsayılan değerini olarak kaydeder.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Bir bağımlılık özelliğinin nasıl ve neden uygulanacağı hakkında daha fazla bilgi için, yalnızca bir CLR özelliğinin özel bir alanla yedeklenmesinin aksine, bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Nasıl Yapılır Konuları](properties-how-to-topics.md)
