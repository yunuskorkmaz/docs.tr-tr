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
ms.openlocfilehash: c5f315992e8ae37bc79602e6986d90e7af591fb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186543"
---
# <a name="custom-animations-overview"></a>Özel Animasyonlara Genel Bakış
Bu konu, özel anahtar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çerçeveleri, animasyon sınıfları oluşturarak veya atlama için çerçeve başına geri arama kullanarak animasyon sistemini nasıl ve ne zaman genişleteceklerini açıklar.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, animasyonlar tarafından sağlanan farklı türde aşina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]olmalıdır. Daha fazla bilgi için, Bkz. From/To/By Animasyonlar Genel Bakış, [Anahtar Kare Animasyonlar Genel Bakış](key-frame-animations-overview.md)ve Yol [Animasyonları Genel Bakış](path-animations-overview.md).  
  
 Animasyon sınıfları <xref:System.Windows.Freezable> sınıftan devraldığından, nesnelere ve 'den <xref:System.Windows.Freezable> <xref:System.Windows.Freezable>nasıl devralınacaklarına aşina olmalısınız. Daha fazla bilgi için [Freezable Objects Genel Bakış'a](../advanced/freezable-objects-overview.md)bakın.  
  
<a name="extendingtheanimationsystem"></a>
## <a name="extending-the-animation-system"></a>Animasyon Sistemini Genişletme  
 Kullanmak istediğiniz yerleşik işlevsellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeyine bağlı olarak animasyon sistemini genişletmenin birkaç yolu vardır.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animasyon altyapısında üç ana genişletilebilirlik noktası vardır:  
  
- Tür>Anahtar Çerçevesi sınıflarından birinden devralarak özel bir anahtar <xref:System.Windows.Media.Animation.DoubleKeyFrame>kare nesnesi oluşturun. * \< * Bu yaklaşım, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon altyapısının yerleşik işlevselliğinin çoğunu kullanır.  
  
- Type>AnimationBase sınıflarından <xref:System.Windows.Media.Animation.AnimationTimeline> veya bunlardan birini devralarak kendi animasyon sınıfınızı oluşturun. * \< *  
  
- Kare başına animasyonlar oluşturmak için kare başına geri arama kullanın. Bu yaklaşım, animasyon ve zamanlama sistemini tamamen atlar.  
  
 Aşağıdaki tabloda animasyon sistemi genişletmek için bazı senaryolar açıklanmaktadır.  
  
|Ne zaman isterseniz ...|Bu yaklaşımı kullanın|  
|-------------------------|-----------------------|  
|Karşılık gelen * \<Tür>* AnimasyonuUsingKeyFrames olan bir tür değerleri arasındaki enterpolasyonu özelleştirme|Özel bir anahtar çerçevesi oluşturun. Daha fazla bilgi için [Özel Anahtar Kare Oluştur](#createacustomkeyframe) bölümüne bakın.|  
|Karşılık gelen * \<Bir Tür>* Animasyonu olan bir türün değerleri arasındaki enterpolasyonu daha fazla özelleştirin.|Animasyon oluşturmayı istediğiniz türe karşılık gelen * \<>* AnimasyonTabanı sınıfından devralan özel bir animasyon sınıfı oluşturun. Daha fazla bilgi için [Özel Animasyon Sınıfı Oluştur](#createacustomanimationtype) bölümüne bakın.|  
|Karşılık gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonu olmayan bir türü canlandırma|Bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıf kullanın veya 'den <xref:System.Windows.Media.Animation.AnimationTimeline>devralan bir sınıf oluşturun. Daha fazla bilgi için [Özel Animasyon Sınıfı Oluştur](#createacustomanimationtype) bölümüne bakın.|  
|Her karede hesaplanan ve son nesne etkileşimkümesini temel alan değerlerle birden çok nesneyi canlandırma|Kare başına geri arama kullanın. Daha fazla bilgi için Çerçeve [Başına Kullanım Geri Arama](#useperframecallback) sı bölümüne bakın.|  
  
<a name="createacustomkeyframe"></a>
## <a name="create-a-custom-key-frame"></a>Özel Anahtar Çerçevesi Oluşturma  
 Özel bir anahtar kare sınıfı oluşturmak, animasyon sistemini genişletmenin en basit yoludur. Anahtar kare animasyonu için farklı bir enterpolasyon yöntemi istediğinizde bu yaklaşımı kullanın.  Anahtar Kare [Animasyonlarına Genel Bakış'ta](key-frame-animations-overview.md)açıklandığı gibi, anahtar kare animasyonu çıkış değerlerini oluşturmak için anahtar kare nesnelerini kullanır. Her anahtar kare nesnesi üç işlev gerçekleştirir:  
  
- Özelliğini <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> kullanarak hedef değeri belirtir.  
  
- Bu değere <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özelliğini kullanarak ulaşılması gereken zamanı belirtir.  
  
- EnterpolateValueCore yöntemini uygulayarak önceki anahtar çerçevenin değeri ile kendi değeri arasında interpolasyonlar.  
  
 **Uygulama Talimatları**  
  
 * \<>KeyFrame *özet sınıfından türetin ve EnterpolateValueCore yöntemini uygulayın. EnterpolateValueCore yöntemi anahtar çerçevenin geçerli değerini döndürür. İki parametre alır: önceki anahtar çerçevenin değeri ve 0 ile 1 arasında değişen bir ilerleme değeri. 0 ilerleme anahtar çerçeve nin yeni başladığını gösterir ve 1 değeri anahtar çerçevenin yeni tamamlandığını ve <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliği tarafından belirtilen değeri döndürmesi gerektiğini gösterir.  
  
 Tür>Anahtar Çerçeve sınıfları <xref:System.Windows.Freezable> sınıftan devraldığından, sınıfınızın yeni bir örneğini döndürmek için çekirdeği de geçersiz kılmanız <xref:System.Windows.Freezable.CreateInstanceCore%2A> gerekir. * \< * Sınıf verilerini depolamak için bağımlılık özelliklerini kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; Daha fazla bilgi için [Freezable Objects Genel Bakış'a](../advanced/freezable-objects-overview.md) bakın.  
  
 Özel * \<Type>* KeyFrame animasyonunuzu oluşturduktan sonra, bu tür için>AnimasyonkullanmaKeyFrames * \<ile *kullanabilirsiniz.  
  
<a name="createacustomanimationtype"></a>
## <a name="create-a-custom-animation-class"></a>Özel Animasyon Sınıfı Oluşturma  
 Kendi animasyon türünü oluşturmak, animasyonlu bir nesnenin nasıl olduğu üzerinde daha fazla denetim sağlar. Kendi animasyon türünüzü oluşturmanın önerilen iki yolu vardır: <xref:System.Windows.Media.Animation.AnimationTimeline> sınıftan veya * \<>* AnimasyonBase sınıfından türetebilirsiniz. >Animasyon veya * \<>Animasyon *Uyrması'ndan türemesi tavsiye edilmezUsingKeyFrames sınıfları. * \< *  
  
### <a name="derive-from-typeanimationbase"></a>Type>\<AnimationBase'den türetin  
 Bir Type>AnimationBase sınıfından türeyen yeni bir animasyon türü oluşturmak için en basit yoludur. * \< * Zaten karşılık gelen * \<Bir Tür>* AnimationBase sınıfına sahip tür için yeni bir animasyon oluşturmak istediğinizde bu yaklaşımı kullanın.  
  
 **Uygulama Talimatları**  
  
 Tür>Animasyon sınıfından türetin ve GetCurrentValueCore yöntemini uygulayın. * \< * GetCurrentValueCore yöntemi animasyonun geçerli değerini döndürür. Üç parametre alır: önerilen başlangıç değeri, önerilen <xref:System.Windows.Media.Animation.AnimationClock>bitiş değeri ve animasyonun ilerlemesini belirlemek için kullandığınız bir , bir.  
  
 Tür>AnimasyonBase sınıfları <xref:System.Windows.Freezable> sınıftan devraldığından, <xref:System.Windows.Freezable.CreateInstanceCore%2A> sınıfınızın yeni bir örneğini döndürmek için çekirdeği de geçersiz kılmanız gerekir. * \< * Sınıf verilerini depolamak için bağımlılık özelliklerini kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; Daha fazla bilgi için [Freezable Objects Genel Bakış'a](../advanced/freezable-objects-overview.md) bakın.  
  
 Daha fazla bilgi için, animasyon yapmak istediğiniz tür için * \<>* AnimasyonBase sınıfının GetCurrentValueCore yöntem belgelerine bakın. Örneğin, [Özel Animasyon Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation) bakın  
  
 **Alternatif Yaklaşımlar**  
  
 Yalnızca,>'in Türü Anahtar Çerçeve sınıflarından birinden türemeyi göz önünde bulundurarak animasyon değerlerinin nasıl enterpolasyona tabi olduğunu değiştirmek istiyorsanız. * \< * Oluşturduğunuz anahtar çerçevesi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] * \< *ilgili Tür>AnimasyonusingKeyFrames tarafından sağlanan kullanılabilir.  
  
### <a name="derive-from-animationtimeline"></a>AnimationTimeline'dan türe  
 Zaten eşleşen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Media.Animation.AnimationTimeline> bir animasyonu olmayan bir tür için animasyon oluşturmak istediğinizde veya güçlü bir şekilde yazılmayan bir animasyon oluşturmak istediğinizde sınıftan türetin.  
  
 **Uygulama Talimatları**  
  
 Sınıftan <xref:System.Windows.Media.Animation.AnimationTimeline> türetin ve aşağıdaki üyeleri geçersiz kılın:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A>– Yeni sınıfınız somutsa, <xref:System.Windows.Freezable.CreateInstanceCore%2A> sınıfınızın yeni bir örneğini döndürmek için geçersiz kılmanız gerekir.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>– Animasyonunuzun geçerli değerini döndürmek için bu yöntemi geçersiz kılın. Üç parametre alır: varsayılan başlangıç değeri, varsayılan <xref:System.Windows.Media.Animation.AnimationClock>hedef değeri ve bir . Animasyon <xref:System.Windows.Media.Animation.AnimationClock> için geçerli zamanı veya ilerlemeyi elde etmek için kullanın. Varsayılan kaynak ve hedef değerlerini kullanıp kullanmamayı seçebilirsiniz.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>– Animasyonunuzun <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> yöntemtarafından belirtilen varsayılan hedef değerini kullanıp kullanmadığını belirtmek için bu özelliği geçersiz kılın.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>– Animasyonunuzun ürettiği <xref:System.Type> çıktıyı belirtmek için bu özelliği geçersiz kılın.  
  
 Sınıf verilerini depolamak için bağımlılık özelliklerini kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; Daha fazla bilgi için [Freezable Objects Genel Bakış'a](../advanced/freezable-objects-overview.md) bakın.  
  
 Önerilen paradigma (animasyonlar tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanılan) iki kalıtım düzeyleri kullanmaktır:  
  
1. 'den <xref:System.Windows.Media.Animation.AnimationTimeline>türeyen soyut * \< *bir Tür>AnimasyonBase sınıfı oluşturun Bu sınıf <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> yöntemi geçersiz kılmalıdır. Ayrıca yeni bir soyut yöntem, GetCurrentValueCore tanıtmak <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> ve varsayılan başlangıç değeri ve varsayılan hedef değer parametreleri türlerini doğrular, sonra GetCurrentValueCore çağırır geçersiz kılar.  
  
2. Yeni * \<Type>* AnimationBase sınıfınızdan devralan ve <xref:System.Windows.Freezable.CreateInstanceCore%2A> yöntemi, tanıttığınız GetCurrentValueCore yöntemini ve <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> özelliği geçersiz kılan başka bir sınıf oluşturun.  
  
 **Alternatif Yaklaşımlar**  
  
 Gelen/To/By animasyonu veya anahtar kare animasyonu olmayan bir türü canlandırmak istiyorsanız, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>bir . Zayıf bir şekilde yazıldığı <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> için, bir değer in her türlüsünün animasyonu olabilir. Bu yaklaşımın dezavantajı <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sadece ayrık enterpolasyon destekler.  
  
<a name="useperframecallback"></a>
## <a name="use-per-frame-callback"></a>Kare Başına Geri Arama Kullanma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animasyon sistemini tamamen atlamanız gerektiğinde bu yaklaşımı kullanın. Bu yaklaşım için bir senaryo, her animasyon adımında animasyonlu nesnelerin yeni bir yönünün veya konumunun son nesne etkileşimkümesine göre yeniden hesaplanması gereken fizik animasyonlarıdır.  
  
 **Uygulama Talimatları**  
  
 Bu genel bakışta açıklanan diğer yaklaşımların aksine, çerçeve başına geri arama kullanmak için özel bir animasyon veya anahtar kare sınıfı oluşturmanız gerekmez.  
  
 Bunun yerine, animasyon <xref:System.Windows.Media.CompositionTarget.Rendering> yapmak istediğiniz nesneleri içeren nesnenin olayı için kaydolursunuz. Bu olay işleyicisi yöntemi çerçeve başına bir kez çağrılır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Görsel ağaçtaki kalıcı görüntüleme verilerini kompozisyon ağacının karşısındaki her zaman, olay işleyicisi yönteminiz çağrılır.  
  
 Olay işleyicinizde, animasyon efektiniz için gereken hesaplamaları gerçekleştirin ve bu değerlerle animasyon yapmak istediğiniz nesnelerin özelliklerini ayarlayın.  
  
 Geçerli çerçevenin sunu saatini elde <xref:System.EventArgs> etmek için, bu olayla <xref:System.Windows.Media.RenderingEventArgs>ilişkili olan <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> oyuncu, geçerli çerçevenin oluşturma süresini elde etmek için kullanabileceğiniz bir özellik sağlayan olarak döküm lenebilir.  
  
 Daha fazla bilgi <xref:System.Windows.Media.CompositionTarget.Rendering> için sayfaya bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Yol Animasyonlarına Genel Bakış](path-animations-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Özel Animasyon Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
