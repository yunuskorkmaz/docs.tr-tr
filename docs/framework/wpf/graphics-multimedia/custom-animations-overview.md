---
title: "Özel Animasyonlara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb8dcce1d72991a803d8a068f29cd0fe3430fdfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-animations-overview"></a>Özel Animasyonlara Genel Bakış
Bu konuda nasıl ve ne zaman açıklanmaktadır genişletmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistemi özel anahtar çerçeveler, animasyon sınıfları oluşturarak veya onu atlamak için çerçeve başına geri çağırma kullanarak.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için farklı türdeki tarafından sağlanan animasyonları aşina olmalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Daha fazla bilgi için bkz: u animasyonlarına genel bakış [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)ve [yol animasyonlarına genel bakış](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Animasyon sınıfları öğesinden devraldığı <xref:System.Windows.Freezable> sınıfı, olmanız gerekir aşina <xref:System.Windows.Freezable> nesneleri ve devralmak nasıl <xref:System.Windows.Freezable>. Daha fazla bilgi için bkz: [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Animasyon sistemini genişletme  
 Bir genişletmek için çeşitli yöntemler vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanmak istediğiniz yerleşik işlevsellik düzeyine bağlı olarak, animasyon sistemi.  Üç birincil genişletilebilirlik noktaları vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon altyapısı:  
  
-   Birinden devralarak özel anahtar çerçeve nesnesi oluşturun  *\<türü >*gibi ana kare sınıfları <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Bu yaklaşım yerleşik işlevselliğinin çoğunu kullanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon altyapısı.  
  
-   Devralarak kendi animasyon sınıfınızı oluşturma <xref:System.Windows.Media.Animation.AnimationTimeline> veya biri  *\<türü >*AnimationBase sınıfları.  
  
-   Çerçeve başına geri çağırma çerçeve başına temelinde animasyonları oluşturmak için kullanın. Bu yaklaşım animasyon ve zamanlama sistemini tamamen atlar.  
  
 Aşağıdaki tabloda bazı animasyon sistemini genişletmek için senaryolar açıklanmaktadır.  
  
|İstediğinizde...|Bu yaklaşımı kullanın|  
|-------------------------|-----------------------|  
|Karşılık gelen bir türü değerleri arasında ilişkilendirme özelleştirme  *\<türü >*AnimationUsingKeyFrames|Özel anahtar çerçevesi oluşturun. Daha fazla bilgi için bkz: [bir özel anahtar çerçeve oluşturma](#createacustomkeyframe) bölümü.|  
|Karşılık gelen bir türün değerleri arasında ilişkilendirmeden birden fazla özelleştirme  *\<türü >*animasyon.|Öğesinden devralınan özel animasyon sınıfı oluşturma  *\<türü >*hale getirmeyi istediğiniz türüne karşılık gelen AnimationBase sınıfı. Daha fazla bilgi için bkz: [özel animasyon sınıfı oluşturma](#createacustomanimationtype) bölümü.|  
|Karşılık gelen olan bir türü animasyon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon|Kullanım bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> veya öğesinden devralınan bir sınıf oluşturun <xref:System.Windows.Media.Animation.AnimationTimeline>. Daha fazla bilgi için bkz: [özel animasyon sınıfı oluşturma](#createacustomanimationtype) bölümü.|  
|Her hesaplanan değerlere sahip birden çok nesne çerçeve ve nesne etkileşimlerin son kümesini temel animasyon olarak oluşturmak|Çerçeve başına geri çağırma kullanın. Daha fazla bilgi için bkz: [bir kullanım çerçeve başına geri çağırma oluşturun](#useperframecallback) bölümü.|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Özel anahtar çerçevesi oluşturun  
 Bir özel anahtar çerçeve sınıfı oluşturma, animasyon sistemini genişletmek için kolay bir yoludur. Bir anahtar çerçeve animasyonu için farklı ilişkilendirme yöntemi istediğinizde bu yaklaşımı kullanın.  Bölümünde açıklandığı gibi [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), çıkış değerleri oluşturmak için bir anahtar çerçeve animasyon anahtar çerçeve nesneleri kullanır. Her anahtar çerçeve nesnesi üç işlevleri gerçekleştirir:  
  
-   Kullanarak bir hedef değer belirtir, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliği.  
  
-   Bu değerin erişilmesi kullanarak süreyi belirtir, <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özelliği.  
  
-   Önceki anahtar çerçevesinin ve kendi değerleri arasında InterpolateValueCore yöntemi uygulayarak ilişkilendirileceğini.  
  
 **Uygulama yönergeleri**  
  
 Öğesinden türetilen  *\<türü >*ana kare soyut sınıf ve InterpolateValueCore yöntemini uygulayın. InterpolateValueCore yöntemi anahtar çerçevenin geçerli değerini döndürür. İki parametre alır: değeri önceki anahtar çerçevesi ve 0 ile 1 olarak değişen bir ilerleme değeri. Anahtar çerçevenin başlatıldığını ve 1 değeri anahtar çerçevenin tamamladığını ve tarafından belirtilen değeri döndürmelidir gösterir 0 ilerlemesini gösterir, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliği.  
  
 Çünkü  *\<türü >*ana kare sınıfları <xref:System.Windows.Freezable> sınıfı, ayrıca kılmanız gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> sınıfının yeni bir örneğini döndürmesi için çekirdek. Sınıf verilerini saklamak için bağımlılık özellikleri'ni kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; bkz: [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) daha fazla bilgi için.  
  
 Özel oluşturduktan sonra  *\<türü >*animasyon ana kare, kullanabileceğiniz ile  *\<türü >*AnimationUsingKeyFrames türü için.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Özel animasyon sınıfı oluşturma  
 Kendi animasyon nasıl nesneyi animasyonlu üzerinde daha fazla denetim türü verir oluşturuluyor. Kendi animasyon türü oluşturmak için önerilen iki yolu vardır: öğesinden türetilen <xref:System.Windows.Media.Animation.AnimationTimeline> sınıfı veya  *\<türü >*AnimationBase sınıfı. Türetme  *\<türü >*animasyon veya  *\<türü >*AnimationUsingKeyFrames sınıfları önerilmez.  
  
### <a name="derive-from-typeanimationbase"></a>Öğesinden türetilen \<türü > AnimationBase  
 Öğesinden türetilen bir  *\<türü >*AnimationBase sınıfı olan yeni bir animasyon türü oluşturmak için en basit yolu. Karşılık gelen zaten türü için yeni bir animasyon oluşturmak istediğinizde bu yaklaşımı kullanın  *\<türü >*AnimationBase sınıfı.  
  
 **Uygulama yönergeleri**  
  
 Öğesinden türetilen bir  *\<türü >*animasyon sınıfı ve GetCurrentValueCore yöntemini uygulayın. GetCurrentValueCore yöntemi animasyonun geçerli değerini döndürür. Üç parametre alır: Önerilen Başlangıç değeri, önerilen bir bitiş değeri ve bir <xref:System.Windows.Media.Animation.AnimationClock>, hangi animasyonun ilerlemesini belirlemek için kullanın.  
  
 Çünkü  *\<türü >*AnimationBase sınıfları <xref:System.Windows.Freezable> sınıfı, ayrıca kılmanız gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> çekirdek, sınıfının yeni bir örneğini döndürür. Sınıf verilerini saklamak için bağımlılık özellikleri'ni kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; bkz: [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) daha fazla bilgi için.  
  
 Daha fazla bilgi için GetCurrentValueCore yöntemi belgelerine bakın  *\<türü >*animasyon eklemek istediğiniz türü için AnimationBase sınıfı. Bir örnek için bkz: [özel animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Alternatif yaklaşımlar**  
  
 Animasyon değerlerinin nasıl ilişkilendirileceğini değiştirmek istiyorsanız, birinden türettikten dikkate  *\<türü >*ana kare sınıfları. Karşılık gelen ile oluşturduğunuz anahtar çerçeve kullanılabilir  *\<türü >*AnimationUsingKeyFrames tarafından sağlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>AnimationTimeline'dan Türetme  
 Öğesinden türetilen <xref:System.Windows.Media.Animation.AnimationTimeline> sınıf eşleşen bir zaten sahip olmayan bir tür için bir animasyon oluşturmak istediğinizde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon veya değil kesin türü belirtilmiş bir animasyon oluşturmak istiyorsanız.  
  
 **Uygulama yönergeleri**  
  
 Öğesinden türetilen <xref:System.Windows.Media.Animation.AnimationTimeline> sınıfı ve aşağıdaki üyeleri geçersiz kılın:  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A>– Yeni sınıfınız somut ise, geçersiz kılmanız gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> , sınıfının yeni bir örneğini dönün.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>– Animasyon geçerli değeri döndürmek için bu yöntemi geçersiz kılın. Üç parametre alır: varsayılan kaynak değeri, varsayılan hedef değer ve bir <xref:System.Windows.Media.Animation.AnimationClock>. Kullanım <xref:System.Windows.Media.Animation.AnimationClock> geçerli zamanı veya animasyonun ilerlemesini elde edilir. Varsayılan kaynak ve hedef değerler kullanmayı seçebilirsiniz.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>– Animasyon tarafından belirtilen varsayılan hedef değeri kullanıp kullanmadığını belirtmek için bu özelliği geçersiz <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> yöntemi.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>– Belirtmek için bu özelliği geçersiz kılma <xref:System.Type> animasyon çıkışı üretir.  
  
 Sınıf verilerini saklamak için bağımlılık özellikleri'ni kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektiriyorsa, ek yöntemleri geçersiz kılmanız gerekebilir; bkz: [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) daha fazla bilgi için.  
  
 Önerilen kip (tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları) iki devralma düzeyi kullanmaktır:  
  
1.  Bir Özet oluşturma  *\<türü >*türetilen AnimationBase sınıfı <xref:System.Windows.Media.Animation.AnimationTimeline>. Bu sınıf kılmalıdır <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> yöntemi. Ayrıca yeni soyut bir yöntem olan GetCurrentValueCore'u, ve geçersiz kılma <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> varsayılan kaynak değerinin türlerini ve varsayılan hedef değer parametreleri doğrular böylece GetCurrentValueCore çağırır.  
  
2.  Devralınan başka bir sınıf oluşturun, yeni gelen  *\<türü >*AnimationBase sınıfı ve geçersiz kılmalar <xref:System.Windows.Freezable.CreateInstanceCore%2A> yöntemi, size sunulan GetCurrentValueCore yöntemi ve <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> özelliği.  
  
 **Alternatif yaklaşımlar**  
  
 Hiçbir karşılık gelen From/To/By animasyonu veya anahtar çerçeve animasyon olan bir türü animasyon eklemek isterseniz, kullanmayı bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Yazılı zayıf olduğu için bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> herhangi türde bir değer animasyon ekleyebilirsiniz. Bu yaklaşımın dezavantajı olan <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> yalnızca ayrık ilişkilendirme destekler.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Çerçeve başına geri çağırma kullanın  
 Tamamen atlamak istediğinizde bu yaklaşımı kullanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistemi. Bir senaryo için bu yaklaşım fizik animasyonları, burada her animasyonu yeniden hesaplanacaktır gereken yeni yönü veya animasyonlu nesnelerin konumunu adım nesne etkileşimlerin son kümesini temel dayalıdır.  
  
 **Uygulama yönergeleri**  
  
 Bu genel bakışta açıklanan diğer yaklaşımlardan farklı olarak, çerçeve başına geri çağırma kullanmak için bir özel animasyon veya anahtar çerçeve sınıfı oluşturmak gerekmez.  
  
 Bunun yerine, için kaydolun <xref:System.Windows.Media.CompositionTarget.Rendering> hale getirmeyi istediğiniz nesneleri içeren nesneyi olay. Bu olay işleyicisi yöntemi çerçeve başına bir kez çağrılır. Her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sıraladığında verilerini kalıcı işleme arasında görsel ağaç birleşim ağacında, olay işleyicisi yöntemi için çağrılır.  
  
 Olay işleyicisi gerçekleştirin hesaplamalar için animasyon gerekli efekt ve bu değerlerle hale getirmeyi istediğiniz nesnelerin özelliklerini ayarlayın.  
  
 Geçerli çerçevenin sunu zamanını elde etmek için <xref:System.EventArgs> bu ile ilişkili olay şeklinde dönüştürülür <xref:System.Windows.Media.RenderingEventArgs>, sağlayan bir <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> geçerli çerçeve elde etmek için kullanabileceğiniz özelliği işleme süresini.  
  
 Daha fazla bilgi için bkz: <xref:System.Windows.Media.CompositionTarget.Rendering> sayfası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.IKeyFrame>  
 [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Yol Animasyonlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animasyon ve Zamanlama Sistemine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Özel animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=159981)
