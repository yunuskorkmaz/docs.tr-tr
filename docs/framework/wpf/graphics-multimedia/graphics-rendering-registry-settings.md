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
ms.openlocfilehash: c3544769480a45068be0ca64e90f91253daf3e16
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629781"
---
# <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları
Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları etkileyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik işleme kayıt defteri ayarlarına genel bir bakış sağlar.  

<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Grafik Işleme kayıt defteri ayarları ne zaman kullanılır?  
 Bu kayıt defteri ayarları, sorun giderme, hata ayıklama ve ürün desteği amacıyla sağlanır. Kayıt defterindeki değişiklikler tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları etkilediğinden, uygulamanız bu kayıt defteri anahtarlarını hiçbir şekilde otomatik olarak veya yükleme sırasında değiştirmemelidir.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>XPDM ve WDDM nedir?  
 Grafik işleme kayıt defteri ayarlarından bazıları, video kartınızın bir XPDM veya WDDM Sürücüsü kullanıp kullanmadığına bağlı olarak farklı varsayılan değerlere sahiptir. XPDM, görüntüleme sürücüsü modeli ve WDDM Windows görüntüleme sürücüsü modelidir. [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] WDDM, ve [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] [!INCLUDE[win7](../../../../includes/win7-md.md)]çalıştıran bilgisayarlarda kullanılabilir. XPDM,, ve [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]çalıştıran bilgisayarlarda kullanılabilir. WDDM hakkında daha fazla bilgi için bkz. [Windows Vista görüntü sürücüsü modeli tasarım kılavuzu](https://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Kayıt defteri ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oluşturmayı denetlemek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için dört kayıt defteri ayarı sağlar:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Donanım hızlandırma seçeneğini devre dışı bırak**|Donanım hızlandırmasının etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|**Maksimum çok örnekli değer**|3-b içeriğini düzgünleştirmek için çoklu örnekleme derecesini belirtir.|  
|**Gerekli video sürücüsü tarih ayarı**|Sistemin donanım hızlandırmasını 2004 Kasım 'Dan önce yayınlanan sürücüler için devre dışı bırakıp bırakmadığını belirtir.|  
|**Başvuru tarayıcısı seçeneğini kullanma**|Başvuru tarayıcısının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanılması gerekip gerekmediğini belirtir.|  
  
 Bu ayarlara, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kayıt defteri ayarlarına nasıl başvurulacağını bilen herhangi bir dış yapılandırma yardımcı programı tarafından erişilebilir. Bu ayarlar ayrıca, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] kayıt defteri Düzenleyicisi kullanılarak değerlere doğrudan erişerek oluşturulabilir veya değiştirilebilir.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Donanım hızlandırma seçeneğini devre dışı bırak  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Donanım hızlandırmasını devre dışı bırak seçeneği** , hata ayıklama ve test amaçları için donanım hızlandırmasını kapatmanıza olanak sağlar. Bir uygulamada yapıtları gördüğünüzde, donanım hızlandırmasını kapatmayı deneyin. Yapıt kaybolursa, sorun video sürücünüzde olabilir.  
  
 **Donanım hızlandırmasını devre dışı bırak seçeneği** 0 veya 1 olan bir DWORD değeridir. 1 değeri donanım hızlandırmasını devre dışı bırakır. 0 değeri, sistemin donanım hızlandırma gereksinimlerini karşıladığından, donanım hızlandırmayı mümkün bir şekilde sunar; daha fazla bilgi için bkz. [grafik Işleme katmanları](../advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Maksimum çok örnekli değer  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **En fazla çoklu örnek değeri** , 3-b içeriğin en yüksek düzgünleştirme miktarını ayarlamanıza olanak sağlar. Üzerinde 3-b düzgünleştirme [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] devre dışı bırakmak veya etkinleştirmek [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]için bu düzeyi kullanın.  
  
 **En fazla MultiSample değeri** , 0 ile 16 arasında DEĞIŞEN bir DWORD değeridir. 0 değeri, 3-b içeriğin çok örnekli düzgünleştirmesinin devre dışı bırakılacağını ve 16 değerinin, video kartı tarafından destekleniyorsa, en çok 16X çoklu örnek düzgünleştirme kullanmayı deneyeceği belirtir. XPDM sürücülerini kullanan bilgisayarlarda bu kayıt defteri anahtarı değerini ayarlamanın, uygulamaların büyük miktarda ek video belleği kullanmasına, 3-b işleme performansını azaltmasına ve işleme hatalarının ve kararlığın tanıtılmasına neden olacağını unutmayın sorunlarının.  
  
 Bu kayıt defteri anahtarı ayarlanmamışsa, XPDM sürücüleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için varsayılan olarak 0, WDDM sürücüleri için 4 olarak ayarlanır.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Gerekli video sürücüsü tarih ayarı  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Dize|  
  
 Kasım 2004 ' de, [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] sürücü sınama yönergelerinin yeni bir sürümünü yayımladı; bu tarihten sonra yazılan sürücüler daha iyi kararlılık sağlar. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu sürücüler için donanım hızlandırma işlem hattını kullanır ve bu tarihten önce yayımlanan XPDM sürücüleri için yazılım işlemeye geri döner.  
  
 **Gerekli video sürücüsü tarih ayarı** , XPDM sürücüleri için alternatif bir en düşük Tarih belirtmenize olanak sağlar. Video sürücünüzün desteklemeye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yetecek kadar kararlı olduğundan emin değilseniz, yalnızca Kasım 2004 ' den önceki bir tarihi belirtmeniz gerekir.  
  
 Gerekli video sürücüsü ayarı aşağıdaki biçimde bir dize alır:  
  
| |  
|-|  
|*YYYY* *AA* GG `/` `/`|  
  
 *Yyyy* dört basamaklı bir yıl, *dd* Iki haneli ay, *gg* ise iki rakamlı gün olur. Bu değer ayarlanmadığında, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gereken video sürücüsü tarihi olarak Kasım, 2004 kullanır.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Başvuru tarayıcısı seçeneğini kullanma  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Başvuru tarayıcısını kullan seçeneği** , hata ayıklama için sanal [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir donanım işleme moduna zorlamanıza olanak sağlar: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım moduna geçer, ancak Microsoft Direct3D Reference yazılım tarayıcısını, d3dref9. dll ' yi kullanır. yerine, gerçek bir donanım cihazı.  
  
 Başvuru tarayıcısı çok yavaştır, ancak sürücü sorunlarından kaynaklanan işleme sorunlarından kaçınmak için video sürücünüzü atlar. Bu nedenle, işleme sorunlarının video sürücüsünden kaynaklanıp kaynaklanmadığını anlamak için başvuru tarayıcısını kullanabilirsiniz. D3dref9. dll dosyası, uygulamanın, sistem yolundaki herhangi bir konumda veya uygulamanın yerel dizininde olduğu gibi, erişebileceği bir konumda olmalıdır.  
  
 **Başvuru tarayıcısını kullan seçeneği** bir DWORD değeri alır. 0 değeri, başvuru tarayıcısının kullanılmadığını gösterir. Sıfır olmayan başka bir değer, başvuru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarayıcısını kullanmaya zorlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafik İşleme Katmanları](../advanced/graphics-rendering-tiers.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
