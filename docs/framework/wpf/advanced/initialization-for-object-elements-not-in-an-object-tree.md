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
ms.openlocfilehash: 219edcbdb09b4edbd9c5ec31e0def77cce6379bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545538"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Nesne Ağacında Olmayan Nesne Öğelerini Başlatma
Bazı yönlerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] başlatma mantıksal ağaç veya görsel ağaç'ile bağlanmakta o öğeye genellikle Bel işlemlere ertelendi. Bu konuda ya da ağacına bağlı olmayan bir öğe başlatmak için gerekli adımlar açıklanmaktadır.  
  
 
  
## <a name="elements-and-the-logical-tree"></a>Öğeleri ve mantıksal ağacının  
 Bir örneğini oluştururken bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfı kodda, çeşitli yönlerini nesne başlatmanın bilmeniz gereken bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfı olmadığının sınıf oluşturucu çağrılırken, yürütülen kod parçası. Özellikle bir denetim sınıfı için bu denetimin görsel gösterimi çoğunu oluşturucusu tarafından tanımlanmamış. Bunun yerine, görsel gösterimi denetimin şablonu tarafından tanımlanır. Şablon çeşitli kaynaklardan potansiyel olarak gelir ancak Şablon tema stilleri çoğunlukla elde edilir. Şablonları etkili bir şekilde geç bağlama; Denetim düzeni için hazır olana kadar gerekli şablon söz konusu denetime bağlı değil. Ve işleme yüzeyi kökünde bağlandığı mantıksal bir ağaç bağlı kadar denetim düzen için hazır değil. Mantıksal ağaçta tanımlanan tüm alt öğeleri işlenmesi başlatır, kök düzeyinde öğedir.  
  
 Görsel ağaç de bu işlemde yer alır. Şablonlar aracılığıyla görsel ağacının bir parçası olan öğeler, bağlı kadar tam olarak oluşturulur.  
  
 Bu davranış sonuçlarını, bir öğenin tamamlanmış görsel özelliklerini kullanan belirli işlemler ek adımlar gerektirir ' dir. Oluşturulmuş, ancak henüz bir ağacına bağlı bir sınıfın görsel özelliklerini almaya çalışırken, bir örnektir. Örneği için çağrı istiyorsanız <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> üzerinde bir <xref:System.Windows.Media.Imaging.RenderTargetBitmap> ve ağaca bağlanmamış bir öğe geçirme görsel ise ek başlatma adımları tamamlanana kadar bu öğe görsel olarak tam değil.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Öğeyi başlatmak için BeginInit ve EndInit'i kullanma  
 Çeşitli sınıflarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamak <xref:System.ComponentModel.ISupportInitialize> arabirimi. Kullandığınız <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> ve <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> kodunuzda başlatma adımları (özelliğinin ayarlanması işlemeyi etkileyen değerleri gibi) içeren bir bölge belirtmek için arabirim yöntemleri. Sonra <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> çağrılır sırayla düzen sistemi öğenin işlemek ve için örtük bir stil aramaya başlayabilirsiniz.  
  
 Öğe üzerindeki özellikleri ayarlıyorsanız ise bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> sınıf sürümlerini çağırabilirsiniz türetilmiş sınıf, <xref:System.Windows.FrameworkElement.BeginInit%2A> ve <xref:System.Windows.FrameworkElement.EndInit%2A> çevrim yerine <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Örnek kod  
 Aşağıdaki örnek işleme kullanan bir konsol uygulaması örnek kodu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ve <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygun yerleşimini göstermek için dosya <xref:System.Windows.FrameworkElement.BeginInit%2A> ve <xref:System.Windows.FrameworkElement.EndInit%2A> diğer geçici [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] çağrıları işlemeyi etkileyen özellikleri ayarlayın.  
  
 Main işlevi yalnızca örnek gösterilmektedir. İşlevler `Rasterize` ve `Save` (gösterilmez), görüntü işleme ve g/ç ile ilgilenebilmek yardımcı işlevlerdir.  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF İçinde Ağaçlar](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
