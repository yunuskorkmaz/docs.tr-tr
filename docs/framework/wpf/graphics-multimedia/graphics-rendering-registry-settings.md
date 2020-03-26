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
ms.openlocfilehash: 642dfdd784af4b85672cf5b0c8e60079763f4c47
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112290"
---
# <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları
Bu konu, uygulamaları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] etkileyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik oluşturma kayıt defteri ayarlarına genel bir bakış sağlar.  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Grafik Oluşturma Kayıt Defteri Ayarları Ne Zaman Kullanılır?  
 Bu kayıt defteri ayarları sorun giderme, hata ayıklama ve ürün destek amaçları için sağlanır. Kayıt defterindeki değişiklikler tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları etkilediğinden, uygulamanız bu kayıt defteri anahtarlarını hiçbir zaman otomatik olarak veya yükleme sırasında değiştirmemelidir.  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>XPDM ve WDDM nedir?  
 Ekran kartınızın XPDM veya WDDM sürücüsü kullanıp kullanmadığına bağlı olarak, grafik oluşturma kayıt defteri ayarlarının bazıları farklı varsayılan değerlere sahiptir. XPDM, Microsoft Windows XP Görüntülü Ekran Sürücüsü Modeli ve WDDM ise Windows Display Driver Modelidir. WDDM, Windows Vista ve Windows 7 çalıştıran bilgisayarlarda kullanılabilir. XPDM, Windows Vista, Microsoft Windows XP ve Microsoft Windows Server 2003 çalıştıran bilgisayarlarda kullanılabilir. WDDM hakkında daha fazla bilgi için [Windows Display Driver Model (WDDM) Tasarım Kılavuzu'na](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide)bakın.  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Kayıt Defteri Ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]işlemeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetlemek için dört kayıt defteri ayarı sağlar:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Donanım Hızlandırma Seçeneğini Devre Dışı**|Donanım hızlandırmanın etkinlenip etkinleştirilmeyeceğini belirtir.|  
|**Maksimum Çoklu Örnek değeri**|3B içeriğin antialiasing için çoklu örnekleme derecesini belirtir.|  
|**Gerekli Video Sürücü Tarih Ayarı**|Sistemin Kasım 2004'ten önce yayımlanan sürücüler için donanım ivmesini devre dışı bırakıp devre dışı bırakmayacağını belirtir.|  
|**Referans Rasterizer Seçeneğini Kullanın**|Referans rasterizer kullanılıp [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanılmaması gerektiğini belirtir.|  
  
 Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayarlara, kayıt defteri ayarlarına nasıl başvuruleceğini bilen herhangi bir dış yapılandırma yardımcı programı erişebilir. Bu ayarlar, windows kayıt defteri düzenleyicisini kullanarak değerlere doğrudan erişerek de oluşturulabilir veya değiştirilebilir.  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a>Donanım Hızlandırma Seçeneğini Devre Dışı  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Devre dışı bırak donanım hızlandırma seçeneği,** hata ayıklama ve test amacıyla donanım ivmesini kapatmanızı sağlar. Bir uygulamada yapı oluşturmayı gördüğünüzde, donanım ivmesi kapatmayı deneyin. Yapı ortadan kalkarsa, sorun video sürücünüzde olabilir.  
  
 **Devre dışı, donanım hızlandırma seçeneği** 0 veya 1 olan bir DWORD değeridir. 1 değeri donanım ivmesini devre dışı düşürür. Sistemin donanım hızlandırma gereksinimlerini karşılaması koşuluyla, 0 değeri donanım ivmesini sağlar; daha fazla bilgi için [Bkz. Grafik Oluşturma Katmanları.](../advanced/graphics-rendering-tiers.md)  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a>Maksimum Çoklu Örnek değeri  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maksimum çoklu örnek değeri,** 3B içeriğin maksimum antialiasing miktarını ayarlamanızı sağlar. Windows Vista'da 3B antialiasing devre dışı kalmak için bu düzeyi kullanın.  
  
 En **büyük çoklu örnek değeri** 0 ile 16 arasında değişen bir DWORD değeridir. 0 değeri, 3B içeriğin çok örnekli antialiasing devre dışı edilmesi gerektiğini belirtir ve 16 değeri ekran kartı tarafından desteklenen 16x çok örnekli antialiasing kullanmaya çalışacağız. XPDM sürücülerini kullanan bilgisayarlarda bu kayıt defteri anahtar değerinin ayarlanması, uygulamaların büyük miktarda ek video belleği kullanmasına, 3B görüntüleme performansını azaltmasına ve işleme hataları ve kararlılık getirme potansiyeline sahip olmasına neden olacağını dikkat edin Sorun.  
  
 Bu kayıt defteri anahtarı ayarlanmadığında, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XPDM sürücüleri için varsayılan olarak 0 ve WDDM sürücüleri için 4 olarak belirlenmiştir.  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>Gerekli Video Sürücü Tarih Ayarı  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Dize|  
  
 Kasım 2004'te Microsoft, sürücü testi yönergelerinin yeni bir sürümünü yayımladı; bu tarihten sonra yazılan sürücüler daha iyi bir istikrar sunar. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu sürücüler için donanım hızlandırma ardışık hattını kullanır ve bu tarihten önce yayınlanan XPDM sürücüleri için yazılım işlemegeri düşer.  
  
 **Gerekli video sürücüsü tarih ayarı,** XPDM sürücüleri için alternatif bir minimum tarih belirtmenizi sağlar. Video sürücünüzün destekleyecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kadar kararlı olduğundan eminseniz, yalnızca Kasım 2004'ten önce bir tarih belirtmeniz gerekir.  
  
 Gerekli video sürücüsü ayarı aşağıdaki biçimde bir dize alır:  
  
| |  
|-|  
|*YYYY* `/` *MM* `/` *DD*|  
  
 *YYYY* dört basamaklı yıl, *MM* iki basamaklı ay ve *DD* iki basamaklı gün. Bu değer ayarlandığında, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gerekli video sürücüsü tarihi olarak Kasım 2004'i kullanır.  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>Referans Rasterizer Seçeneğini Kullanın  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Kullanım referans rasterizer seçeneği** hata [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayıklama için simüle donanım işleme moduna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zorlamak için izin verir: donanım moduna gider, ancak microsoft direct3D referans yazılımı rasterizer, d3dref9.dll, gerçek bir donanım aygıtı yerine kullanır.  
  
 Referans rasterizer çok yavaş, ancak sürücü sorunları nedeniyle herhangi bir render sorunları önlemek için video sürücüsü atlar. Bu nedenle, oluşturma sorunlarının video sürücüsünden kaynaklanıp kaynaklanmamasA da başvuruda bulunabilirsiniz. d3dref9.dll dosyası, sistem yolundaki herhangi bir konumda veya uygulamanın yerel dizininde olduğu gibi uygulamanın bu dosyaya erişebileceği bir konumda olmalıdır.  
  
 **Kullanım başvurusu rasterizer seçeneği** bir DWORD değeri alır. 0 değeri, referans rasterizer kullanılmadığını gösterir. Referans rasterizer kullanmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için diğer sıfır olmayan değer kuvvetleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafik İşleme Katmanları](../advanced/graphics-rendering-tiers.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
