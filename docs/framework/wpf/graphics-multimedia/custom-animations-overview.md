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
ms.openlocfilehash: b97c926da28eeb5385de71362a6cbc064ccc20cd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615434"
---
# <a name="custom-animations-overview"></a>Özel Animasyonlara Genel Bakış
Bu konu nasıl ve ne zaman açıklar genişletmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistem özel anahtar çerçeveler, animasyon sınıfları oluşturarak veya onu atlamak için çerçeve başına geri çağırma kullanarak.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için farklı türdeki tarafından sağlanan animasyonları tanımanız gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Daha fazla bilgi için bkz: u animasyonlarına genel bakış [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md)ve [yol animasyonlarına genel bakış](path-animations-overview.md).  
  
 Animasyon sınıfları <xref:System.Windows.Freezable> sınıfı olmanız gerekir aşina <xref:System.Windows.Freezable> nesneleri ve devralınacak nasıl <xref:System.Windows.Freezable>. Daha fazla bilgi için [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Animasyon sistemini genişletme  
 Birçok genişletin yoldan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanmak istediğiniz yerleşik işlevsellik düzeyine bağlı olarak, animasyon sistemi.  Üç birincil genişletilebilirlik noktaları vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon altyapısı:  
  
- Birinden devralan bir özel anahtar çerçeve nesnesi oluşturma  *\<türü >* gibi ana kare sınıfları <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Bu yaklaşım yerleşik işlevselliğinin kullanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon altyapısı.  
  
- Kendi animasyon sınıfı devralarak oluşturma <xref:System.Windows.Media.Animation.AnimationTimeline> veya biri  *\<türü >* AnimationBase sınıfları.  
  
- Çerçeve başına geri çağırma çerçeve başına temelinde animasyonları oluşturmak için kullanın. Bu yaklaşım, animasyon ve zamanlama sistemi tamamen atlar.  
  
 Aşağıdaki tabloda, bazı animasyon sistemini genişletmek için senaryoları açıklar.  
  
|Ne yapmak istiyorsunuz?|Bu yaklaşımı kullanın|  
|-------------------------|-----------------------|  
|Karşılık gelen bir tür değerleri arasında enterpolasyon özelleştirme  *\<türü >* AnimationUsingKeyFrames|Özel anahtar çerçevesi oluşturun. Daha fazla bilgi için [bir özel anahtar çerçeve oluşturma](#createacustomkeyframe) bölümü.|  
|Daha fazlasını karşılık gelen bir tür değerleri arasında enterpolasyon özelleştirme  *\<türü >* animasyon.|Devralınan özel animasyon sınıfı oluşturma  *\<türü >* animasyon uygulamak istediğiniz türüne karşılık gelen AnimationBase sınıfı. Daha fazla bilgi için [özel animasyon sınıfı oluşturma](#createacustomanimationtype) bölümü.|  
|Karşılık gelen bir yok türü hareketlendirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon|Kullanım bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> veya devralınan bir sınıf oluşturmanız <xref:System.Windows.Media.Animation.AnimationTimeline>. Daha fazla bilgi için [özel animasyon sınıfı oluşturma](#createacustomanimationtype) bölümü.|  
|Her hesaplanan değerlerle birden fazla nesne çerçeve ve son nesne etkileşimlerini kümesini temel alarak Canlandır|Çerçeve başına geri çağırma kullanın. Daha fazla bilgi için [kullanım çerçeve başına geri çağırma oluşturun](#useperframecallback) bölümü.|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Özel bir anahtar kare oluşturma  
 Bir özel anahtar çerçeve sınıfı oluşturmak, animasyon sistemini genişletmek için kolay bir yoludur. Farklı ilişkilendirme yöntemi için bir anahtar çerçeve animasyonu istediğinizde bu yaklaşımı kullanın.  Bölümünde anlatıldığı gibi [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md), çıkış değerleri oluşturmak için anahtar çerçeve nesneleri anahtar çerçeve animasyonu kullanır. Her bir ana kare nesne üç işlevleri gerçekleştirir:  
  
- Kullanarak bir hedef değer belirtir, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliği.  
  
- Başlangıçtan bu değeri erişilmesi kullanarak süreyi belirtir, <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özelliği.  
  
- Değeri, önceki anahtar çerçeve ile kendi değerine arasında InterpolateValueCore yöntem uygulanarak ilişkilendirir.  
  
 **Uygulama yönergeleri**  
  
 Öğesinden türetilen  *\<türü >* ana kare soyut sınıf ve InterpolateValueCore yöntemini uygulayın. Anahtar çerçevesi'nin geçerli değeri InterpolateValueCore yöntemini döndürür. İki parametre alır: değeri önceki anahtar çerçeve ve 0 ile 1 arasında bir ilerleme değeri. Anahtar çerçeve başladığına ve anahtar çerçeve tamamladığını ve ile belirtilen değer döndürmelidir 1 değerini gösterir 0 ilerlemesini gösterir, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliği.  
  
 Çünkü  *\<türü >* ana kare sınıfları <xref:System.Windows.Freezable> sınıfı, ayrıca kılmanız gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> çekirdeğini sınıfınıza yeni bir örneğini döndürür. Sınıf verilerini depolamak için bağımlılık özellikleri kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektirirse, ek yöntemleri geçersiz kılmanız gerekebilir; bkz: [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md) daha fazla bilgi için.  
  
 Kendi özel oluşturduktan sonra  *\<türü >* ana kare animasyon kullanabileceğiniz ile  *\<türü >* AnimationUsingKeyFrames türü için.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Özel animasyon sınıfı oluşturma  
 Daha fazla nesneyi animasyonlu üzerinde nasıl denetim türü verir kendi animasyon oluşturuluyor. Kendi animasyon türü oluşturmak için önerilen iki yolu vardır: türetebilirsiniz <xref:System.Windows.Media.Animation.AnimationTimeline> sınıfı veya  *\<türü >* AnimationBase sınıfı. Öğesinden türetme  *\<türü >* animasyon veya  *\<türü >* AnimationUsingKeyFrames sınıfları önerilmez.  
  
### <a name="derive-from-typeanimationbase"></a>Öğesinden türetilen \<türü > AnimationBase  
 Türetilen bir  *\<türü >* AnimationBase sınıfı, yeni bir animasyon türü oluşturmak için en basit yolu. Zaten olan bir karşılık gelen bir tür için yeni bir animasyon oluşturmak istiyorsanız bu yaklaşımı kullanın  *\<türü >* AnimationBase sınıfı.  
  
 **Uygulama yönergeleri**  
  
 Öğesinden türetilen bir  *\<türü >* animasyon sınıfı ve GetCurrentValueCore yöntemini uygulayın. GetCurrentValueCore yöntemi animasyon geçerli değerini döndürür. Üç parametreleri alır: önerilen bir başlangıç değeri, önerilen bir bitiş değeri ve bir <xref:System.Windows.Media.Animation.AnimationClock>, animasyonun ilerleme durumunu belirlemek için kullanın.  
  
 Çünkü  *\<türü >* AnimationBase sınıfları <xref:System.Windows.Freezable> sınıfı, ayrıca kılmanız gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> çekirdeğini sınıfınıza yeni bir örneğini döndürür. Sınıf verilerini depolamak için bağımlılık özellikleri kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektirirse, ek yöntemleri geçersiz kılmanız gerekebilir; bkz: [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md) daha fazla bilgi için.  
  
 Daha fazla bilgi için GetCurrentValueCore yöntemi belgelerine bakın  *\<türü >* animasyon uygulamak istediğiniz türe ilişkin AnimationBase sınıfı. Bir örnek için bkz [özel animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Alternatif yaklaşımlar**  
  
 Animasyon değerlerini nasıl ilişkilendirileceğini değiştirmek istiyorsanız, birinden türettikten dikkate  *\<türü >* ana kare sınıfları. Oluşturduğunuz anahtar çerçeve ile ilgili kullanılabilir  *\<türü >* AnimationUsingKeyFrames sağladığı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>AnimationTimeline'dan Türetme  
 Öğesinden türetilen <xref:System.Windows.Media.Animation.AnimationTimeline> sınıf zaten eşleşen bir sahip olmayan bir tür için bir animasyon oluşturmak istediğinizde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon veya türü kesin belirlenmiş değil bir animasyon oluşturmak istiyorsanız.  
  
 **Uygulama yönergeleri**  
  
 Öğesinden türetilen <xref:System.Windows.Media.Animation.AnimationTimeline> sınıfı ve aşağıdaki üyeleri geçersiz kıl:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A> – Yeni sınıfınıza somut ise, geçersiz kılmanız gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> sınıfınıza yeni bir örneğini dönün.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – Animasyonunuzu geçerli değerini döndürmek için bu yöntemi yok sayın. Üç parametreleri alır: varsayılan kaynak değeri, varsayılan hedef değer ve bir <xref:System.Windows.Media.Animation.AnimationClock>. Kullanım <xref:System.Windows.Media.Animation.AnimationClock> geçerli zamanı veya animasyon için devam eden elde edilir. Varsayılan kaynak ve hedef değerleri kullanılıp kullanılmayacağını seçebilirsiniz.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – Animasyonunuzu tarafından belirtilen varsayılan hedef değer kullanıp kullanmadığını göstermek için bu özelliği geçersiz kılma <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> yöntemi.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – Belirtmek için bu özelliği geçersiz kılma <xref:System.Type> animasyonunuzu çıktısı üretir.  
  
 Sınıf verilerini depolamak için bağımlılık özellikleri kullanmıyorsa veya oluşturulduktan sonra ek başlatma gerektirirse, ek yöntemleri geçersiz kılmanız gerekebilir; bkz: [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md) daha fazla bilgi için.  
  
 Önerilen paradigma (tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları) iki devralma düzeyleri kullanmaktır:  
  
1. Bir soyut oluşturma  *\<türü >* türetildiği AnimationBase sınıfı <xref:System.Windows.Media.Animation.AnimationTimeline>. Bu sınıf'ı geçersiz kılmalıdır <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> yöntemi. Ayrıca yeni soyut bir yöntem olan GetCurrentValueCore'u, ve geçersiz kılma <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> varsayılan hedef değer parametreleri ve varsayılan başlangıç değer türlerini doğrular, böylece daha sonra GetCurrentValueCore çağırır.  
  
2. Devralan başka bir sınıf oluşturmanız gelen yeni  *\<türü >* AnimationBase sınıf ve geçersiz kılmaları <xref:System.Windows.Freezable.CreateInstanceCore%2A> yöntemi, tanıttığınız GetCurrentValueCore yöntemi ve <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> özelliği.  
  
 **Alternatif yaklaşımlar**  
  
 Karşılık gelen From/To/By animasyonu veya anahtar çerçeve animasyonu olmayan bir tür animasyon uygulamak isterseniz kullanmayı bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Zayıf yazılmış, çünkü bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> herhangi bir türde değer animasyon uygulayabilirsiniz. Bu yaklaşımın bir dezavantajı olan <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> yalnızca ayrık ilişkilendirme destekler.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Çerçeve başına geri çağırma kullanın  
 Tamamen atlamak gerektiğinde bu yaklaşımı kullanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistemi. Bu yaklaşıma bir senaryo fizik animasyonları, burada her animasyonu adım yeni veya animasyonlu nesnelerin konumunu yeniden hesaplanmasını gerekiyor nesne etkileşimlerini son kümesinde dayalıdır.  
  
 **Uygulama yönergeleri**  
  
 Bu genel bakışta açıklanan diğer bir yaklaşım, çerçeve başına geri çağırma kullanmak için özel animasyon veya anahtar çerçeve sınıfı oluşturmanız gerekmez.  
  
 Bunun yerine, için kayıt <xref:System.Windows.Media.CompositionTarget.Rendering> olayı animasyon uygulamak istediğiniz nesneleri içeren nesne. Bu olay işleyicisi yöntemi, çerçeve başına bir kez çağrılır. Her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sıraladığında kalıcı işleme verileri arasında görsel ağaç kompozisyon ağacı, olay işleyicisi yönteminiz için çağrılır.  
  
 Olay işleyicisinde, gerçekleştirin, animasyon için gerekli hesaplamalar etkisi yoktur ve bu değerleri ile animasyon uygulamak istediğiniz nesnelerin özelliklerini ayarlayın.  
  
 Geçerli çerçevenin sunu zamanını almak için <xref:System.EventArgs> bununla ilişkili olay olarak yayımlanabilir <xref:System.Windows.Media.RenderingEventArgs>, sağlayan bir <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> geçerli çerçeve elde etmek için kullanabileceğiniz özellik işleme süresini.  
  
 Daha fazla bilgi için <xref:System.Windows.Media.CompositionTarget.Rendering> sayfası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Yol Animasyonlarına Genel Bakış](path-animations-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Özel animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=159981)
