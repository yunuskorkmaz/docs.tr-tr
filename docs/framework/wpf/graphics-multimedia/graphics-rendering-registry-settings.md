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
ms.openlocfilehash: f2cebe8e02a2d8beec659fe4ac81fde2e85f3c1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557725"
---
# <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları
Bu konu genel bir bakış sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] etkileyen kayıt defteri ayarlarını grafik oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  

  
<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Grafik işleme kayıt defteri ayarları kullanmak ne zaman  
 Bu kayıt defteri ayarları, sorun giderme, hata ayıklama ve ürün destek amaçları için sağlanır. Kayıt defterinde değişiklik tüm etkilediğinden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, uygulamanız hiçbir zaman alter bu kayıt defteri anahtarları otomatik olarak veya yükleme sırasında.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>XPDM ve WDDM nedir?  
 Grafik kayıt defteri ayarları işleme bazıları video kartınız bir XPDM veya WDDM sürücüsünü kullanıp kullanmadığını bağlı olarak farklı varsayılan değerlere sahiptir. XPDM [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görüntü sürücüsü modeli ve WDDM olan Windows görüntü sürücüsü modeli. WDDM çalıştıran bilgisayarlarda kullanılabilir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../../includes/win7-md.md)]. XPDM çalıştıran bilgisayarlarda kullanılabilir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], ve [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]. WDDM hakkında daha fazla bilgi için bkz: [Windows Vista görüntü sürücüsü modeli Tasarım Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Kayıt defteri ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört kayıt defteri ayarlarını denetlemek için sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Donanım hızlandırma seçeneği devre dışı bırak**|Donanım hızlandırma etkin olup olmadığını belirtir.|  
|**En büyük çoklu örneklem değeri**|Düzgünleştirmek için çoklu örnekleme derecesini belirtir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği.|  
|**Gerekli ekran kartı sürücüsü tarih ayarı**|Sistem Kasım 2004'ten önce yayımlanan sürücüler için donanım hızlandırmasını devre dışı bırakır olup olmadığını belirtir.|  
|**Başvuru tarayıcısını seçeneği kullanma**|Belirtir olup olmadığını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanmanız gerekir.|  
  
 Bu ayarların nasıl başvurulacağını bildiği bir dış yapılandırma yardımcı programı tarafından erişilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kayıt defteri ayarları. Bu ayarları da oluşturulabilir veya değerleri kullanarak doğrudan erişerek [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Kayıt Defteri Düzenleyicisi'ni.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Donanım hızlandırma seçeneği devre dışı bırak  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Donanım hızlandırma seçeneği devre dışı** hata ayıklama ve test amaçları için donanım hızlandırmasını devre dışı bırakmak üzere sağlar. Bir uygulamada işleme yapıların gördüğünüzde, donanım hızlandırmasını devre dışı bırakmak deneyin. Yapı kaybolursa, sorunu, video sürücüsü ile olabilir.  
  
 **Donanım hızlandırma seçeneği devre dışı** , 0 veya 1 olan bir DWORD değeridir. 1 değeri, donanım hızlandırmasını devre dışı bırakır. Sistem donanım hızlandırma gereksinimlerini karşılaması koşuluyla 0 değeri, donanım hızlandırmasını sağlar; Daha fazla bilgi için bkz: [grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>En büyük çoklu örneklem değeri  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maksimum çoklu örneklem değeri** düzgünleştirme en fazla ayarlamanıza olanak tanır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği. Bu düzey devre dışı bırakma [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] düzgünleştirme içinde [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] veya içinde etkinleştirmek [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  
  
 **Maksimum çoklu örneklem değeri** 0 ile 16 arasında değişen bir DWORD değeri. 0 değeri, 3-b içeriğinin çoklu örneklem düzgünleştirme devre dışı bırakılmalıdır ve 16 değerinin 16 x'çoklu örneklem düzgünleştirme kullanmaya video kartı tarafından desteklenirse çalışır belirtir. Bu kayıt defteri anahtarı değerini XPDM sürücülerini kullanan bilgisayarlarda ayarı uygulamaların büyük miktarda ek ekran belleği kullanmasına, düşmesine neden olur dikkat [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] oluşturma ve işleme hatalara olanağına sahiptir ve kararlılık sorunları.  
  
 Bu kayıt defteri anahtarı ayarlanmadığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XPDM sürücüleri için 0 ve 4 WDDM sürücüleri için varsayılan olarak yükler.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Gerekli ekran kartı sürücüsü tarih ayarı  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Dize|  
  
 Kasım, 2004, [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] yayımlanan yönergeleri sınama sürücüsü yeni bir sürümünü; tarihi bu teklif daha iyi kararlılık sonra yazılan sürücüler. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım hızlandırma ardışık düzeni için bu sürücüleri kullanır ve yazılım sürücüleri için işlemeye bu tarihten önce yayımlanan XPDM döner.  
  
 **Video sürücüsü tarih ayarı gerekli** XPDM sürücüleri için alternatif bir minimum tarih belirtmenize olanak sağlar. Video sürücüsü desteklemek için kararlı olduğundan eminseniz yalnızca Kasım 2004'den önceki bir tarih belirtmelisiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Gerekli ekran kartı sürücüsü ayarı aşağıdaki biçimde bir dize alır:  
  
||  
|-|  
|*YYYY* `/` *MM* `/` *GG*|  
  
 Burada *YYYY* dört rakamlı yıl *MM* iki basamaklı ay ve *GG* iki basamaklı günüdür. Bu değer ayarlanmadığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kasım 2004 kendi gerekli ekran kartı sürücüsü tarihini olarak kullanır.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Başvuru tarayıcısını seçeneği kullanma  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Başvuru tarayıcısını seçeneği kullanma** zorlamak sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hata ayıklama için bir sanal donanım işleme moduna: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım moduna girer, ancak kullanır [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] yazılım tarayıcısı, başvuru gerçek donanım aygıtı yerine d3dref9.dll.  
  
 Görüntüleyiciye çok yavaştır, ancak sürücü sorunlarından kaynaklanan işleme sorunlarını önlemek için video sürücünüzü atlar. Bu nedenle, görüntüleyiciye işleme sorunlarını video sürücüsü tarafından neden olup olmadığını belirlemek için kullanabilirsiniz. D3dref9.dll dosya, uygulama, gibi herhangi bir konumda sistem yolunda veya yerel dizin uygulamanın erişebildiği bir konumda olması gerekir.  
  
 **Başvuru tarayıcısını seçeneği kullanma** bir DWORD değeri alır. 0 değeri, görüntüleyiciye kullanılmadığını belirtir. Diğer bir sıfır olmayan bir değer zorlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanılacak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik İşleme Katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
