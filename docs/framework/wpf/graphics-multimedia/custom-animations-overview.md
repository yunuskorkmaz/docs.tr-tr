---
title: Özel Animasyonlara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
ms.openlocfilehash: 5a9ca51b87f73a24b90d0bd843ee306f8a1b970a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453097"
---
# <a name="custom-animations-overview"></a>Özel Animasyonlara Genel Bakış
Bu konu, özel anahtar çerçeveler, animasyon sınıfları oluşturarak veya bunu atlamak için çerçeve başına geri çağırma kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sisteminin nasıl ve ne zaman genişletileceğini açıklar.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tarafından sunulan farklı animasyon türleri hakkında bilgi sahibi olmanız gerekir. Daha fazla bilgi için bkz. From/To/By animasyonlara genel bakış, [anahtar çerçeve Animasyonlarına Genel](key-frame-animations-overview.md)bakış ve [yol animasyonlara genel](path-animations-overview.md)bakış.  
  
 Animasyon sınıfları <xref:System.Windows.Freezable> sınıfından devraldığı için, <xref:System.Windows.Freezable> nesneleri ve <xref:System.Windows.Freezable>nasıl devraldığı hakkında bilgi sahibi olmanız gerekir. Daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Animasyon sistemini genişletme  
 Kullanmak istediğiniz yerleşik işlevselliğin düzeyine bağlı olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistemini genişletmek için çeşitli yollar vardır.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon altyapısında üç birincil genişletilebilirlik noktası vardır:  
  
- <xref:System.Windows.Media.Animation.DoubleKeyFrame>gibi *\<türü >* ana kare sınıflarından birinden devralarak özel bir anahtar çerçeve nesnesi oluşturun. Bu yaklaşım [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon altyapısının yerleşik işlevlerinin çoğunu kullanır.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline> veya *\<türünden birini >* AnimationBase sınıflarından devralarak kendi animasyon sınıfınızı oluşturun.  
  
- Çerçeve başına, animasyon oluşturmak için kare başına geri çağırma kullanın. Bu yaklaşım, animasyon ve zamanlama sistemini tamamen atlar.  
  
 Aşağıdaki tabloda, animasyon sisteminin genişlemesiyle ilgili bazı senaryolar açıklanmaktadır.  
  
|İstediğiniz zaman...|Bu yaklaşımı kullanın|  
|-------------------------|-----------------------|  
|Karşılık gelen bir *\<türüne*sahip bir türün değerleri arasındaki ilişkilendirmeyi Özelleştirme > AnimationUsingKeyFrames|Özel bir anahtar çerçevesi oluşturun. Daha fazla bilgi için [özel anahtar çerçevesi oluşturma](#createacustomkeyframe) bölümüne bakın.|  
|Karşılık gelen *\<türü >* animasyonuna sahip olan bir türün değerleri arasında ilişkilendirmeden fazlasını özelleştirin.|Hareketlendirmek istediğiniz türe karşılık gelen *\<türü >* AnimationBase sınıfından devralan özel bir animasyon sınıfı oluşturun. Daha fazla bilgi için [özel animasyon sınıfı oluşturma](#createacustomanimationtype) bölümüne bakın.|  
|Karşılık gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonu olmayan bir türe animasyon ekleme|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> kullanın veya <xref:System.Windows.Media.Animation.AnimationTimeline>devralan bir sınıf oluşturun. Daha fazla bilgi için [özel animasyon sınıfı oluşturma](#createacustomanimationtype) bölümüne bakın.|  
|Her karede hesaplanan ve son nesne etkileşimleri kümesini temel alan değerlerle birden çok nesneye animasyon ekleyin|Çerçeve başına geri çağırma kullanın. Daha fazla bilgi için, [çerçeve başına kullanım çağrısı oluşturma](#useperframecallback) bölümüne bakın.|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Özel anahtar çerçevesi oluşturma  
 Özel anahtar çerçeve sınıfı oluşturmak, animasyon sistemini genişletmenin en kolay yoludur. Anahtar çerçeve animasyonu için farklı bir enterpolasyon yöntemi istediğinizde bu yaklaşımı kullanın.  [Anahtar çerçeve animasyonlara genel bakış](key-frame-animations-overview.md)bölümünde açıklandığı gibi, bir anahtar çerçeve animasyonu çıkış değerlerini oluşturmak için anahtar çerçeve nesnelerini kullanır. Her anahtar çerçeve nesnesi üç işlev gerçekleştirir:  
  
- <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliğini kullanarak bir hedef değer belirtir.  
  
- <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özelliğini kullanarak bu değere erişilmesi gereken süreyi belirtir.  
  
- InterpolateValueCore metodunu uygulayarak önceki anahtar çerçevesinin değeri ile kendi değeri arasında enterpolasyonlar.  
  
 **Uygulama yönergeleri**  
  
 *\<türü >* ana kare soyut sınıfından türetir ve InterpolateValueCore yöntemini uygulayın. InterpolateValueCore yöntemi, anahtar çerçevesinin geçerli değerini döndürür. İki parametre alır: önceki anahtar çerçevesinin değeri ve 0 ile 1 arasında değişen bir ilerleme değeri. 0 ilerlemesi, anahtar çerçevesinin yeni başlatıldığını gösterir ve 1 değeri anahtar çerçevesinin tamamlandığını ve <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliği tarafından belirtilen değeri döndürmesi gerektiğini gösterir.  
  
 *\<türü >* ana kare sınıfları <xref:System.Windows.Freezable> sınıfından devraldığı için, sınıfınızın yeni bir örneğini döndürmek için <xref:System.Windows.Freezable.CreateInstanceCore%2A> çekirdeğini da geçersiz kılmanız gerekir. Sınıf, verilerini depolamak için bağımlılık özelliklerini kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; daha fazla bilgi için [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md) bölümüne bakın.  
  
 Özel *\<türü >* ana kare animasyonunu oluşturduktan sonra, bu türü *\<türü >* AnimationUsingKeyFrames ile kullanabilirsiniz.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Özel bir animasyon sınıfı oluşturma  
 Kendi animasyon türünü oluşturmak, bir nesneye animasyon eklenmiş olarak daha fazla denetim sağlar. Kendi animasyon türünü oluşturmak için önerilen iki yöntem vardır: <xref:System.Windows.Media.Animation.AnimationTimeline> sınıfından veya *\<türü >* AnimationBase sınıfından türetebilirsiniz. *\<türünden türetme >* animasyon veya *\<tür >* AnimationUsingKeyFrames sınıfları önerilmez.  
  
### <a name="derive-from-typeanimationbase"></a>\<türünden türet > AnimationBase  
 *\<türü >* AnimationBase sınıfından türetmek, yeni bir animasyon türü oluşturmanın en kolay yoludur. Karşılık gelen bir *\<türü >* AnimationBase sınıfına zaten sahip olan tür için yeni bir animasyon oluşturmak istediğinizde bu yaklaşımı kullanın.  
  
 **Uygulama yönergeleri**  
  
 Bir *\<türü >* animasyon sınıfından türetebilir ve GetCurrentValueCore yöntemini uygulayın. GetCurrentValueCore yöntemi animasyonun geçerli değerini döndürür. Üç parametre alır: önerilen başlangıç değeri, önerilen bitiş değeri ve animasyonun ilerlemesini belirlemek için kullandığınız <xref:System.Windows.Media.Animation.AnimationClock>.  
  
 *\<türü >* AnimationBase sınıfları <xref:System.Windows.Freezable> sınıfından devraldığı için, sınıfınızın yeni bir örneğini döndürmek için <xref:System.Windows.Freezable.CreateInstanceCore%2A> çekirdeğini da geçersiz kılmanız gerekir. Sınıf, verilerini depolamak için bağımlılık özelliklerini kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; daha fazla bilgi için [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md) bölümüne bakın.  
  
 Daha fazla bilgi için, hareketlendirmek istediğiniz türe ilişkin *\<türü >* AnimationBase sınıfına yönelik GetCurrentValueCore yöntemi belgelerine bakın. Bir örnek için bkz. [özel animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Alternatif yaklaşımlar**  
  
 Yalnızca animasyon değerlerinin nasıl ilişkilendirileceğini değiştirmek istiyorsanız, *\<türünden birini >* ana kare sınıflarından türetmeyi göz önünde bulundurarak. Oluşturduğunuz anahtar çerçeve, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tarafından sunulan karşılık gelen *\<türü >* AnimationUsingKeyFrames ile birlikte kullanılabilir.  
  
### <a name="derive-from-animationtimeline"></a>AnimationTimeline 'dan türet  
 Zaten eşleşen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonuna sahip olmayan bir tür için animasyon oluşturmak istediğinizde veya kesin olarak yazılmamış bir animasyon oluşturmak istiyorsanız <xref:System.Windows.Media.Animation.AnimationTimeline> sınıfından türetebilirsiniz.  
  
 **Uygulama yönergeleri**  
  
 <xref:System.Windows.Media.Animation.AnimationTimeline> sınıfından türet ve aşağıdaki üyeleri geçersiz kıl:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A> – yeni sınıfınız somut ise, sınıfınızın yeni bir örneğini döndürmek için <xref:System.Windows.Freezable.CreateInstanceCore%2A> geçersiz kılmanız gerekir.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – Animasyonunuzun geçerli değerini döndürmek için bu yöntemi geçersiz kılın. Üç parametre alır: varsayılan bir kaynak değeri, varsayılan hedef değeri ve bir <xref:System.Windows.Media.Animation.AnimationClock>. Animasyonun geçerli saatini veya ilerlemesini almak için <xref:System.Windows.Media.Animation.AnimationClock> kullanın. Varsayılan kaynak ve hedef değerlerini kullanıp kullanmayacağınızı seçebilirsiniz.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – Animasyonunuzun <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> yöntemi tarafından belirtilen varsayılan hedef değeri kullanıp kullanmadığını belirtmek için bu özelliği geçersiz kılın.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – Animasyonunuzun ürettiği çıkışın <xref:System.Type> belirtmek için bu özelliği geçersiz kılın.  
  
 Sınıf, verilerini depolamak için bağımlılık özelliklerini kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; daha fazla bilgi için [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md) bölümüne bakın.  
  
 Önerilen paradigma ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları tarafından kullanılır) iki devralma düzeyi kullanmaktır:  
  
1. <xref:System.Windows.Media.Animation.AnimationTimeline>türetilen bir soyut *\<türü >* AnimationBase sınıfı oluşturun. Bu sınıf <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> yöntemi geçersiz kılmalıdır. Ayrıca, varsayılan kaynak değeri ve varsayılan hedef değer parametrelerinin türlerini doğrulamak üzere <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> yeni bir soyut Yöntem, GetCurrentValueCore ve geçersiz kılmalıdır ve sonra GetCurrentValueCore öğesini çağırır.  
  
2. Yeni *\<türünden >* AnimationBase sınıfından devralan başka bir sınıf oluşturun ve <xref:System.Windows.Freezable.CreateInstanceCore%2A> yöntemini, kullanıma aldığınız GetCurrentValueCore yöntemini ve <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> özelliğini geçersiz kılar.  
  
 **Alternatif yaklaşımlar**  
  
 Kendisine karşılık gelen/to/By animasyonuna veya anahtar çerçeve animasyonuna sahip olmayan bir türe animasyon eklemek istiyorsanız, bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>kullanmayı düşünün. Zayıf bir tür olduğundan, bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> her türlü değer için animasyon uygulayabilir. Bu yaklaşımın dezavantajı <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> yalnızca ayrık ilişkilendirmeyi desteklemesidir.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Çerçeve başına geri çağırma kullan  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistemini tamamen atlamak gerektiğinde bu yaklaşımı kullanın. Bu yaklaşım için bir senaryo, her animasyon adımının yeni bir yön veya animasyonlu nesne konumunun son nesne etkileşimleri kümesine göre yeniden hesaplanması gereken fizik animasyonlarıdır.  
  
 **Uygulama yönergeleri**  
  
 Bu genel bakışta açıklanan diğer yaklaşımlardan farklı olarak, çerçeve başına geri çağırma kullanmak için özel bir animasyon veya anahtar çerçeve sınıfı oluşturmanız gerekmez.  
  
 Bunun yerine, hareketlendirmek istediğiniz nesneleri içeren nesnenin <xref:System.Windows.Media.CompositionTarget.Rendering> olayına kaydolabilirsiniz. Bu olay işleyicisi yöntemi çerçeve başına bir kez çağırılır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] her seferinde, görsel ağaçtaki kalıcı işleme verilerini birleşim ağacına her sıraladığında olay işleyicisi yönteminiz çağırılır.  
  
 Olay işleyicinizde, animasyon efektiniz için gereken hesaplamaları gerçekleştirin ve bu değerlerle hareketlendirmek istediğiniz nesnelerin özelliklerini ayarlayın.  
  
 Geçerli çerçevenin sunum süresini elde etmek için, bu olayla ilişkili <xref:System.EventArgs> <xref:System.Windows.Media.RenderingEventArgs>olarak ayarlanabilir, bu da geçerli çerçevenin işleme süresini elde etmek için kullanabileceğiniz bir <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> özelliği sağlar.  
  
 Daha fazla bilgi için <xref:System.Windows.Media.CompositionTarget.Rendering> sayfasına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Yol Animasyonlarına Genel Bakış](path-animations-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Özel animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
