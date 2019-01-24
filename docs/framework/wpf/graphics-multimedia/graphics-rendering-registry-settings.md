---
title: Grafik İşleme Kayıt Defteri Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: 020570c66401661f55b82a0c7111b4ac53f9c884
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556161"
---
# <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları
Bu konu, genel bir bakış sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik etkileyen kayıt defteri ayarları oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  

  
<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Grafik işleme kayıt defteri ayarları kullanmak ne zaman  
 Bu kayıt defteri ayarları, sorun giderme, hata ayıklama ve ürün destek amaçları için sağlanır. Kayıt defterindeki değişiklikleri tüm etkilediğinden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, uygulamanız hiçbir zaman alter bu kayıt defteri anahtarları otomatik olarak veya yükleme sırasında.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>XPDM ve WDDM nelerdir?  
 Grafik işleme kayıt defteri ayarları bazıları video kartınız bir XPDM veya WDDM sürücüsünü kullanıp kullanmadığını bağlı olarak farklı varsayılan değerlere sahiptir. XPDM [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görüntü sürücü modeli ve WDDM olan Windows görüntü sürücüsü modeli. WDDM çalıştıran bilgisayarlarda kullanılabilir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../../includes/win7-md.md)]. XPDM çalıştıran bilgisayarlarda kullanılabilir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], ve [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]. WDDM hakkında daha fazla bilgi için bkz. [Windows Vista görünen sürücü Model Tasarım Kılavuzu](https://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Kayıt defteri ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört kayıt defteri ayarlarını denetlemek için sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Donanım hızlandırma seçeneği devre dışı bırak**|Donanım hızlandırma etkin olup olmadığını belirtir.|  
|**Çoklu örneklem en yüksek değer**|Düzgünleştirmek için çoklu örnekleme derecesini belirtir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği.|  
|**Video sürücüsü gerekli tarih ayarı**|Sistem Kasım 2004'ten önce yayımlanan sürücüler için donanım hızlandırmasını devre dışı bırakır olup olmadığını belirtir.|  
|**Başvuru tarayıcısını seçeneğini kullanın**|Belirtir olup olmadığını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanmanız gerekir.|  
  
 Bu ayarları dosyasına nasıl başvurulacağı bildiği bir dış yapılandırma yardımcı programı tarafından erişilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kayıt defteri ayarları. Bu ayarlar da oluşturulabilir veya değerleri kullanarak doğrudan erişerek [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Kayıt Defteri Düzenleyicisi.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Donanım hızlandırma seçeneği devre dışı bırak  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Donanım hızlandırma seçeneği devre dışı** hata ayıklama ve test amaçlı donanım hızlandırmasını devre dışı bırakmak sağlar. Bir uygulamada işleme yapıların gördüğünüzde, donanım hızlandırmasını devre dışı bırakmak deneyin. Yapıt kaybolursa, sorun, bir video sürücüsü ile olabilir.  
  
 **Donanım hızlandırma seçeneği devre dışı** 0 veya 1 bir DWORD değeri. 1 değeri, donanım hızlandırmasını devre dışı bırakır. Sistem donanım hızlandırma gereksinimleri karşılaması koşuluyla 0 değerini donanım hızlandırmasını sağlar; Daha fazla bilgi için [grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Çoklu örneklem en yüksek değer  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Çoklu örneklem maksimum değer** düzgünleştirme en uzun süreyi ayarlamanıza olanak tanır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği. Bu düzey devre dışı bırakma [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içinde düzgünleştirme [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] veya içinde etkinleştirmek [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  
  
 **Çoklu örneklem maksimum değer** 0 ile 16 arasında değişen bir DWORD değeri. 0 değeri, 3B içeriği çoklu örneklem düzgünleştirme devre dışı bırakılmalıdır ve 16 değerini 16 x çoklu örneklem düzgünleştirme kullanmayı video kartı tarafından destekleniyorsa dener belirtir. XPDM sürücüleri kullanan bilgisayarlarda bu kayıt defteri anahtarı değerini ayarlama uygulamaların çok miktarda ek video bellek kullanmasına, düşmesine neden olur sıralamaların [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] oluşturma ve işleme hatalara olanağına sahiptir ve kararlılık sorunlarını.  
  
 Bu kayıt defteri anahtarı olarak ayarlanmadığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XPDM sürücüleri için 0 ile 4 WDDM sürücüler için varsayılan değeri.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Video sürücüsü gerekli tarih ayarı  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Dize|  
  
 Kasım, 2004'te [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] yayımlanan yönergeleri test sürücü yeni bir sürümü; tarihi bu teklifi daha iyi kararlılık sonra yazılan sürücüler. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım hızlandırma ardışık düzeni için bu sürücüleri kullanır ve bu tarihten önce yayımlanmış XPDM sürücüleri yazılımla işleme için döner.  
  
 **Video sürücüsü tarih ayarı gerekli** XPDM sürücüleri için alternatif en az bir tarih belirtmenizi sağlar. Yalnızca, bir video sürücüsü desteklemek için kararlı olduğunu eminseniz Kasım 2004'ten önceki bir tarihi belirtmelidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Gerekli bir video sürücüsü ayarı aşağıdaki biçimi dizesini alır:  
  
| |  
|-|  
|*YYYY* `/` *MM* `/` *EKLE*|  
  
 Burada *YYYY* dört basamaklı yıl *MM* iki haneli ay ve *GG* iki basamaklı gündür. Bu değer ayarlanmadığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kasım 2004, gerekli bir video sürücüsü tarihi olarak kullanır.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Başvuru tarayıcısını seçeneğini kullanın  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Başvuru tarayıcısını seçeneği kullanma** zorlamanızı sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hata ayıklama için bir sanal donanım oluşturma moduna: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım moduna geçer, ancak kullanır [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] yazılım tarayıcısı başvuru bir gerçek donanım cihazı yerine d3dref9.dll.  
  
 Görüntüleyiciye çok yavaştır, ancak sürücü sorunlar nedeniyle işleme sorunlardan kaçınmak için bir video sürücüsü atlar. Bu nedenle, görüntüleyiciye video sürücüsü tarafından işleme sorunları nedeniyle oluşup oluşmadığını belirlemek için kullanabilirsiniz. Uygulama, gibi herhangi bir konumda sistem yolunda veya uygulamanın yerel dizindeki erişebileceğiniz bir konuma d3dref9.dll dosyası olmalıdır.  
  
 **Başvuru tarayıcısını seçeneği kullanma** bir DWORD değeri alır. 0 değeri, görüntüleyiciye kullanılmadığını gösterir. Diğer bir sıfır olmayan bir değer zorlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanılacak.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Grafik İşleme Katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)
- [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
