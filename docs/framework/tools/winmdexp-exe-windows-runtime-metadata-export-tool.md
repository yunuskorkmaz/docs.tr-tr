---
title: Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7181f6f28d576c5ddbbbe57d27e1d41e412cef6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408105"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] Meta veri verme aracı (Winmdexp.exe) içeren bir dosyayı bir .NET Framework modül dönüştüren [!INCLUDE[wrt](../../../includes/wrt-md.md)] meta verileri. Ancak .NET Framework derlemeleri ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] meta veri dosyaları aynı fiziksel biçimi kullanın, .NET Framework derlemeleri olarak otomatik olarak kullanılabilir olmadığını anlamına gelir meta verileri tabloların içeriğini farklılıklar vardır [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri . .NET Framework modüle kapatma işlemi bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşen olarak adlandırılır *dışarı aktarma*. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], sonuçta ortaya çıkan Windows Meta veriler (.winmd) dosya meta verileri ve uygulama içerir.  
  
 Kullandığınızda  **[!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşen** altında bulunan şablon **Windows mağazası** C# ve Visual Basic'te [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] veya [!INCLUDE[vs_dev11_ext](../../../includes/vs-dev11-ext-md.md)], .winmdobj dosya derleyici hedeflediği ve sonraki derleme adımı .winmdobj dosya .winmd dosyasına dışarı aktarmak için Winmdexp.exe çağırır. Bu, oluşturmak için önerilen yoldur bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni. Oluşturma süreci üzerinde, Visual Studio'nun sağladığından daha fazla kontrol sahibi olmak istediğinizde doğrudan Winmdexp.exe'yi kullanın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
winmdexp [options] winmdmodule  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız değişken veya seçenek|Açıklama|  
|------------------------|-----------------|  
|`winmdmodule`|Dışarı aktarılacak modülü (.winmdobj) belirtir. Yalnızca tek bir modüle izin verilir. Bu modül oluşturmak üzere kullanmanız `/target` derleyici seçeneği ile `winmdobj` hedef. Bkz: [/target: winmdobj (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) veya [/target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Winmdexp.exe'nin üreteceği çıktı XML belgesi dosyasını belirtir. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], çıktı dosyası temelde giriş XML belge dosyası ile aynıdır.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Derleyici ile üretilen XML belge dosyası adını belirtir `winmdmodule`.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Simgelerini içeren program veritabanı (PDB) dosya adını belirtir `winmdmodule`.|  
|`/nowarn:``warning`|Belirtilen uyarı sayısını gizler. İçin *uyarı*, hata kodu, yalnızca sayısal kısmı sıfırları olmadan sağlayın.|  
|`/out:``file`<br /><br /> `/o:``file`|Windows meta veri (.winmd) çıktı dosyasının adını belirtir.|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Dışarı aktarılan Windows meta veri (.winmd) dosyası için sembolleri içeren çıktı program veritabanı (PDB) dosyasının adını belirtir.|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Dışarı aktarma sırasında başvurulacak bir meta veri dosyasını (.winmd veya derleme) belirtir. Başvuru derlemelerde kullanıyorsanız, "\Program dosyaları (x86) \Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5 "(" \Program Files\\... "32-bit bilgisayarlarda), hem System.Runtime.dll hem de mscorlib.dll başvurular içerir.|  
|`/utf8output`|Çıktı iletilerinde UTF-8 kodlamasının kullanılması gerektiğini belirtir.|  
|`/warnaserror+`|Tüm uyarıların hata sayılması gerektiğini belirtir.|  
|**@** `responsefile`|Seçenekleri içeren bir yanıt (.rsp) dosyası belirtir (ve isteğe bağlı olarak `winmdmodule`). Her satırda `responsefile` tek bağımsız değişken veya seçenek içermelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Winmdexp.exe, rasgele bir .NET Framework derlemesini .winmd dosyasına dönüştürmek için tasarlanmamıştır. İle derlenen bir modülü gerektirir `/target:winmdobj` seçeneği ve ek kısıtlamalar uygulanır. Derlemenin API yüzeyi sunulan tüm türler olmalıdır kısıtlamalarının en önemli olan [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri. Daha fazla bilgi için makalenin "Windows çalışma zamanı bileşenleri türlerinde bildirme" bölümüne bakın [C# ve Visual Basic Windows çalışma zamanı bileşenleri oluşturma](http://go.microsoft.com/fwlink/p/?LinkID=238313) Windows geliştirme Merkezi'ndeki.  
  
 Yazdığınız zaman bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama veya bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni C# veya Visual Basic ile .NET Framework ile programlama yapmak için destek sağlar [!INCLUDE[wrt](../../../includes/wrt-md.md)] daha doğal. Bu makalede açıklanan [Windows mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). Bazı yaygın olarak kullanılan işleminde, [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri için .NET Framework türleri eşlendi. Winmdexp.exe bu işlem tersine çevirir ve karşılık gelen kullanan bir API yüzeyi üretir [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri. Örneğin, gelen oluşturulan türleri <xref:System.Collections.Generic.IList%601> gelen oluşturulan türleri için arabirim eşlemesi [!INCLUDE[wrt](../../../includes/wrt-md.md)] [IVector\<T >](http://go.microsoft.com/fwlink/p/?LinkId=251132)arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](http://go.microsoft.com/fwlink/p/?LinkID=238313)  
 [Winmdexp.exe Hata İletileri](../../../docs/framework/tools/winmdexp-exe-error-messages.md)  
 [Yapı, dağıtım ve yapılandırma araçları (.NET Framework)](http://msdn.microsoft.com/library/b8c921be-6012-4181-b8d4-ab15813fc9a7)
