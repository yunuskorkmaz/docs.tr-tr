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
ms.openlocfilehash: f1d31a5916f0c2a1763d8f24076ae7c1000a8296
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376383"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Nesne Ağacında Olmayan Nesne Öğelerini Başlatma
Bazı yönlerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] başlatma erteleneceğini mantıksal ağaç veya görsel ağaç'için bağlı bu öğe genellikle kullanan işlemler. Bu konu, ya da ağacına bağlı olmayan bir öğe başlatmak için gereken adımları açıklar.  
  
 
  
## <a name="elements-and-the-logical-tree"></a>Öğeleri ve mantıksal ağaç  
 Örneği oluşturduğunuzda, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfı kod içinde çeşitli yönlerini nesne başlatmanın bilmeniz gereken bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfı kasıtlı bir parçası değildir sınıf oluşturucusu çağrılırken yürütülen kod. Özellikle bir denetim sınıf için denetimin görsel temsilini çoğunu Oluşturucu tarafından tanımlanmadı. Bunun yerine, görsel bir temsili denetim şablonu tarafından tanımlanır. Şablon olabilecek çeşitli kaynaklardan gelir, ancak çoğunlukla şablonu tema stillerinden elde edilir. Şablonları etkili bir şekilde geç bağlama; Denetim için Düzen hazır olana kadar gerekli şablon söz konusu denetime bağlı değil. Ve kökünde bir işleme yüzeyi bağlanan bir mantıksal ağaç bağlı olduğu kadar denetim için Düzen hazır değil. Mantıksal ağaçta tanımlanan tüm alt öğeleri işleme başlatır, kök düzeyinde öğesidir.  
  
 Görsel ağacı da bu işlemde yer alır. Şablonları aracılığıyla görsel ağacın bir parçası olan öğeler, bağlı kadar tam olarak örneği oluşturulur.  
  
 Sonuçları, bu davranış, bir öğenin tamamlanmış görsel özelliklerini kullanan belirli işlemleri ek adımlar gerektirmez ' dir. Bir sınıfın oluşturulmuş, ancak henüz bir ağaca bağlı görsel özelliklerini almak çalışırken, bir örnektir. Örneğin, çağrı istiyorsanız <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> üzerinde bir <xref:System.Windows.Media.Imaging.RenderTargetBitmap> ve, kaçı görsel ağaç olarak bağlı olmayan bir öğedir ek başlatma adımlar tamamlanana kadar bu öğenin görsel olarak tam değil.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Öğeyi başlatmak için BeginInit ve EndInit'i kullanma  
 Çeşitli sınıflarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamak <xref:System.ComponentModel.ISupportInitialize> arabirimi. Kullandığınız <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> ve <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> kodunuzda başlatma adımları (özellik ayarı işlemeyi etkileyen değerleri gibi) içeren bir bölge göstermek için arabirimin yöntemlerini. Sonra <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> çağrılır sırayla düzen sistemi öğe işleyebilir ve örtülü bir stil için aramaya başlayabilirsiniz.  
  
 Öğe özellikleri üzerinde ayarladığınız bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> sınıf sürümlerini çağırabilirsiniz türetilmiş bir sınıf, <xref:System.Windows.FrameworkElement.BeginInit%2A> ve <xref:System.Windows.FrameworkElement.EndInit%2A> atamayı yerine <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Örnek Kod  
 Aşağıdaki örnek, işleme kullanan bir konsol uygulaması için örnek kod [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ve <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygun yerleşimini göstermek için dosya <xref:System.Windows.FrameworkElement.BeginInit%2A> ve <xref:System.Windows.FrameworkElement.EndInit%2A> diğer etrafında [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] çağrıları Bu işleme etkileyen özelliklerini ayarlayın.  
  
 Main işlevi yalnızca örnek gösterir. İşlevleri `Rasterize` ve `Save` görüntü işleme ve g/ç ilgileniriz yardımcı program işlevleri olan (gösterilmemiştir).  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF İçinde Ağaçlar](trees-in-wpf.md)
- [WPF Grafik İşlemeye Genel Bakış](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
