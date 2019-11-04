---
title: Nesne Ağacında Olmayan Nesne Öğelerini Başlatma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: 1a1d956ee7f41ac1ac0fc9bd051a18b9ff438930
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459841"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Nesne Ağacında Olmayan Nesne Öğelerini Başlatma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] başlatmanın bazı yönleri, genellikle mantıksal ağaca veya görsel ağaca bağlı olan öğeyi kullanan işlemlere ertelenir. Bu konu, herhangi bir ağaca bağlı olmayan bir öğeyi başlatmak için gerekli olabilecek adımları açıklamaktadır.  

## <a name="elements-and-the-logical-tree"></a>Öğeler ve mantıksal ağaç  
 Kodda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfının bir örneğini oluşturduğunuzda, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfı için nesne başlatmasının birkaç yönü, sınıf oluşturucusu çağrılırken yürütülen kodun bir parçası değildir. Özellikle bir denetim sınıfı için, bu denetimin görsel gösteriminin çoğu Oluşturucu tarafından tanımlanmamıştır. Bunun yerine, görsel temsili denetimin şablonu tarafından tanımlanır. Şablon, çok çeşitli kaynaklardan gelir, ancak çoğu zaman şablon tema stillerinden elde edilir. Şablonlar etkili bir şekilde geç bağlamadır; gerekli şablon, denetim düzen için hazırlanana kadar söz konusu denetime eklenmez. Ayrıca Denetim, köke bir işleme yüzeyine bağlanan bir mantıksal ağaca iliştirilene kadar, düzen için de kullanıma uygun değildir. Mantıksal ağaçta tanımlanan tüm alt öğelerini işlemeyi Başlatan kök düzeyi öğedir.  
  
 Görsel ağaç Ayrıca bu işleme katılır. Şablonlar aracılığıyla görsel ağacın bir parçası olan öğeler, bağlanana kadar de tam olarak başlatılamaz.  
  
 Bu davranışın sonuçları, bir öğenin tamamlanmış görsel özelliklerine dayanan bazı işlemlerin ek adımlar gerektirmelerdir. Oluşturulan ancak henüz bir ağaca eklenmemiş olan bir sınıfın görsel özelliklerini almaya çalışıyorsanız örnek bir örnektir. Örneğin, bir <xref:System.Windows.Media.Imaging.RenderTargetBitmap> <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> çağırmak isterseniz ve geçirdiğiniz görsel bir ağaca bağlı olmayan bir öğe ise, ek başlatma adımları tamamlanana kadar bu öğe görsel olarak tamamlanmaz.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>BeginInit kullanma ve öğeyi başlatmak için  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli sınıflar <xref:System.ComponentModel.ISupportInitialize> arabirimini uygular. Kodunuzda başlatma adımları içeren bir bölgeyi göstermek için arabirimin <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> ve <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> yöntemlerini (işlemeyi etkileyen özellik değerlerini ayarlama gibi) kullanabilirsiniz. Dizi <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> çağrıldıktan sonra, Düzen sistemi öğeyi işleyebilir ve örtülü bir stil aramaya başlayabilir.  
  
 Üzerinde Özellikler ayarladığınız öğe bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş bir sınıf ise, <xref:System.ComponentModel.ISupportInitialize>atamak yerine <xref:System.Windows.FrameworkElement.BeginInit%2A> ve <xref:System.Windows.FrameworkElement.EndInit%2A> sınıf sürümlerini çağırabilirsiniz.  
  
### <a name="sample-code"></a>Örnek kod  
 Aşağıdaki örnek, <xref:System.Windows.FrameworkElement.BeginInit%2A> uygun yerleşimini ve işlemeyi etkileyen özellikleri ayarlamaya yönelik diğer API çağrılarının etrafında <xref:System.Windows.FrameworkElement.EndInit%2A>, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işleme API 'Leri ve gevşek bir dosya <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> kullanan bir konsol uygulaması için örnek koddur.  
  
 Örnek yalnızca ana işlevi gösterir. `Rasterize` ve `Save` işlevleri (gösterilmez), görüntü işleme ve GÇ 'nin ele aldığı yardımcı işlevlerdir.  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde Ağaçlar](trees-in-wpf.md)
- [WPF Grafik İşlemeye Genel Bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
