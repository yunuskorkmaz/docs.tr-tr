---
title: Grafik İşleme Kayıt Defteri Ayarları
description: Windows Presentation Foundation (WPF) ' de sorun giderme, hata ayıklama ve ürün desteği amaçlarıyla kayıt defteri ayarlarını nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: a2c6cfa5a207ae89c053f6ee81597f01458b5933
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853756"
---
# <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları
Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları etkileyen grafik işleme kayıt defteri ayarlarına genel bir bakış sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Grafik Işleme kayıt defteri ayarları ne zaman kullanılır?  
 Bu kayıt defteri ayarları, sorun giderme, hata ayıklama ve ürün desteği amacıyla sağlanır. Kayıt defterindeki değişiklikler tüm uygulamaları etkilediğinden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , uygulamanız bu kayıt defteri anahtarlarını hiçbir şekilde otomatik olarak veya yükleme sırasında değiştirmemelidir.  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>XPDM ve WDDM nedir?  
 Grafik işleme kayıt defteri ayarlarından bazıları, video kartınızın bir XPDM veya WDDM Sürücüsü kullanıp kullanmadığına bağlı olarak farklı varsayılan değerlere sahiptir. XPDM, Microsoft Windows XP görüntü sürücüsü modeli ve WDDM Windows görüntüleme sürücüsü modelidir. WDDM, Windows Vista ve Windows 7 çalıştıran bilgisayarlarda kullanılabilir. XPDM, Windows Vista, Microsoft Windows XP ve Microsoft Windows Server 2003 çalıştıran bilgisayarlarda kullanılabilir. WDDM hakkında daha fazla bilgi için bkz. [Windows görüntü sürücü modeli (WDDM) Tasarım Kılavuzu](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide).  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Kayıt Defteri Ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oluşturmayı denetlemek için dört kayıt defteri ayarı sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
|Ayar|Description|  
|-------------|-----------------|  
|**Donanım hızlandırma seçeneğini devre dışı bırak**|Donanım hızlandırmasının etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|**Maksimum çok örnekli değer**|3B içeriğini düzgünleştirme için çoklu örnekleme derecesini belirtir.|  
|**Gerekli video sürücüsü tarih ayarı**|Sistemin donanım hızlandırmasını 2004 Kasım 'Dan önce yayınlanan sürücüler için devre dışı bırakıp bırakmadığını belirtir.|  
|**Başvuru tarayıcısı seçeneğini kullanma**|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Başvuru tarayıcısının kullanılması gerekip gerekmediğini belirtir.|  
  
 Bu ayarlara, kayıt defteri ayarlarına nasıl başvurulacağını bilen herhangi bir dış yapılandırma yardımcı programı tarafından erişilebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Bu ayarlar, Windows kayıt defteri Düzenleyicisi kullanılarak değerlere doğrudan erişerek da oluşturulabilir veya değiştirilebilir.  
  
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
  
 **Maksimum çoklu örnek değeri** , 3B içeriğin en yüksek düzgünleştirme miktarını ayarlamanıza olanak sağlar. Windows Vista 'da 3B düzgünleştirmenin devre dışı bırakılması için bu düzeyi kullanın.  
  
 **En fazla MultiSample değeri** , 0 ile 16 arasında DEĞIŞEN bir DWORD değeridir. 0 değeri, 3B içeriklerin çoklu örnek düzgünleştirmesinin devre dışı bırakılacağını ve 16 değerinin, video kartı tarafından destekleniyorsa, en çok 16X çoklu örnek düzgünleştirme kullanmayı deneyeceği belirtir. XPDM sürücülerini kullanan bilgisayarlarda bu kayıt defteri anahtarı değerini ayarlamanın, uygulamaların büyük miktarda ek video belleği kullanmasına, 3B işlemenin performansını azaltmasına ve işleme hataları ve kararlılık sorunlarını ortaya çıkarabilir.  
  
 Bu kayıt defteri anahtarı ayarlanmamışsa, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XPDM sürücüleri için varsayılan olarak 0, WDDM sürücüleri için 4 olarak ayarlanır.  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>Gerekli video sürücüsü tarih ayarı  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Dize|  
  
 Kasım, 2004 ' de, Microsoft sürücü sınama yönergelerinin yeni bir sürümünü yayımladı; Bu tarihten sonra yazılan sürücüler daha iyi kararlılık sağlar. Varsayılan olarak, bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sürücüler için donanım hızlandırma işlem hattını kullanır ve bu tarihten önce YAYıMLANAN XPDM sürücüleri için yazılım işlemeye geri döner.  
  
 **Gerekli video sürücüsü tarih ayarı** , XPDM sürücüleri için alternatif bir en düşük Tarih belirtmenize olanak sağlar. Video sürücünüzün desteklemeye yetecek kadar kararlı olduğundan emin değilseniz, yalnızca Kasım 2004 ' den önceki bir tarihi belirtmeniz gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 Gerekli video sürücüsü ayarı aşağıdaki biçimde bir dize alır:  
  
| |  
|-|  
|*Yyyy* `/` *AA* `/` *gg*|  
  
 *Yyyy* dört basamaklı bir yıl, *dd* Iki haneli ay, *gg* ise iki rakamlı gün olur. Bu değer ayarlanmadığında, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gereken video sürücüsü tarihi olarak Kasım, 2004 kullanır.  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>Başvuru tarayıcısı seçeneğini kullanma  
  
|Kayıt defteri anahtarı|Değer türü|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Başvuru tarayıcısını kullan seçeneği** , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hata ayıklama için sanal bir donanım işleme moduna zorlamanıza olanak sağlar: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım moduna geçer, ancak gerçek bir donanım cihazı yerine Microsoft Direct3D Reference yazılım tarayıcısını d3dref9.dll kullanır.  
  
 Başvuru tarayıcısı çok yavaştır, ancak sürücü sorunlarından kaynaklanan işleme sorunlarından kaçınmak için video sürücünüzü atlar. Bu nedenle, işleme sorunlarının video sürücüsünden kaynaklanıp kaynaklanmadığını anlamak için başvuru tarayıcısını kullanabilirsiniz. d3dref9.dll dosyası, uygulamanın, sistem yolundaki herhangi bir konumda veya uygulamanın yerel dizininde olduğu gibi, erişebileceği bir konumda olmalıdır.  
  
 **Başvuru tarayıcısını kullan seçeneği** bir DWORD değeri alır. 0 değeri, başvuru tarayıcısının kullanılmadığını gösterir. Sıfır olmayan başka bir değer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , başvuru tarayıcısını kullanmaya zorlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafik İşleme Katmanları](../advanced/graphics-rendering-tiers.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
