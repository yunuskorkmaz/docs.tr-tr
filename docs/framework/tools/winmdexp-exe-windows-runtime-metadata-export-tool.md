---
title: Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01cdcbb93fde0d2d2f1c800613d9709da0d695f6
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026009"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
Windows çalışma zamanı meta verileri dışarı aktarma Aracı'nı (Winmdexp.exe) bir .NET Framework modülünü Windows çalışma zamanı meta verileri içeren bir dosyaya dönüştürür. .NET Framework derlemelerinin ve Windows çalışma zamanı meta veri dosyaları aynı fiziksel biçim kullansa da, hangi .NET Framework derlemeleri otomatik Windows çalışma zamanı bileşenleri kullanılabilir olmadığı anlamına gelir meta veri tablolarının içeriğinde farklar vardır . Bir .NET Framework modülünü bir Windows çalışma zamanı bileşeni kapatma işlemi olarak adlandırılır *verme*. .NET Framework 4.5 ve .NET Framework 4.5.1, sonuçta elde edilen Windows meta veri (.winmd) dosyası hem meta veriler hem de uygulama içerir.  
  
 Kullanırken **Windows çalışma zamanı bileşeni** altında bulunan şablon **Windows Store** için C# ve Visual Basic'te Visual Studio 2013 veya Visual Studio 2012, derleyici hedefi bir .winmdobj Dosya ve sonraki Oluşturma adımı .winmdobj dosyasını bir .winmd dosyasına aktarmak için Winmdexp.exe'yi çağırır. Bir Windows çalışma zamanı bileşeni oluşturmak için önerilen yöntem budur. Oluşturma süreci üzerinde, Visual Studio'nun sağladığından daha fazla kontrol sahibi olmak istediğinizde doğrudan Winmdexp.exe'yi kullanın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız değişken veya seçenek|Açıklama|  
|------------------------|-----------------|  
|`winmdmodule`|Dışarı aktarılacak modülü (.winmdobj) belirtir. Yalnızca tek bir modüle izin verilir. Bu modülü oluşturmak için kullanın `/target` derleyici seçeneğiyle `winmdobj` hedef. Bkz: [/target: winmdobj (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) veya [/target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Winmdexp.exe'nin üreteceği çıktı XML belgesi dosyasını belirtir. .NET Framework 4.5, çıktı dosyası temelde girdi XML belgeleme dosyasıyla aynıdır.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Derleyici ile ürettiği XML belgeleme dosyasının adını belirtir `winmdmodule`.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|İçin simgeler içeren program veritabanı (PDB) dosyasının adını belirtir `winmdmodule`.|  
|`/nowarn:``warning`|Belirtilen uyarı sayısını gizler. İçin *uyarı*, başta sıfır bulunmadan tamsayıyı hata kodunun yalnızca sayısal bölümünü sağlayın.|  
|`/out:``file`<br /><br /> `/o:``file`|Windows meta veri (.winmd) çıktı dosyasının adını belirtir.|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Dışarı aktarılan Windows meta veri (.winmd) dosyası için sembolleri içeren çıktı program veritabanı (PDB) dosyasının adını belirtir.|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Dışarı aktarma sırasında başvurulacak bir meta veri dosyasını (.winmd veya derleme) belirtir. Başvuru bütünleştirilmiş kodları içinde kullanıyorsanız "\Program dosyaları (x86) \Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5 "(" \Program dosyaları\\... "32-bit bilgisayarlarda), hem System.Runtime.dll hem de mscorlib.dll için başvuruları içerir.|  
|`/utf8output`|Çıktı iletilerinde UTF-8 kodlamasının kullanılması gerektiğini belirtir.|  
|`/warnaserror+`|Tüm uyarıların hata sayılması gerektiğini belirtir.|  
|**@** `responsefile`|Seçenekleri içeren bir yanıt (.rsp) dosyasını belirtir (ve isteğe bağlı olarak `winmdmodule`). Her satırda `responsefile` tek bağımsız değişken veya seçenek bulunmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Winmdexp.exe, rasgele bir .NET Framework derlemesini .winmd dosyasına dönüştürmek için tasarlanmamıştır. İle derlenmiş bir modül gerektirir `/target:winmdobj` seçeneği ve ek kısıtlamalar uygulanır. Bu kısıtlamaların en önemlisi, derlemenin API yüzeyinde sunulan tüm türleri Windows çalışma zamanı türleri olması gerekliliğidir. Daha fazla bilgi için makalenin "Windows çalışma zamanı bileşenleri türleri bildirme" bölümüne bakın. [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](https://go.microsoft.com/fwlink/p/?LinkID=238313) Windows geliştirme Merkezi'nde.  
  
 Yazdığınızda bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama veya bir Windows çalışma zamanı bileşeni ile C# veya Visual Basic .NET Framework Windows çalışma zamanı ile programlama daha doğal hale getirmek için destek sağlar. Bu makalede açıklanan [Windows Store uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). Bu süreçte bazı yaygın olarak kullanılan bir Windows çalışma zamanı türleri için .NET Framework türleri eşlenir. Winmdexp.exe bu işlemi tersine çevirir ve karşılık gelen Windows çalışma zamanı türlerini kullanan bir API yüzey oluşturur. Örneğin, oluşturulan türler <xref:System.Collections.Generic.IList%601> Windows çalışma zamanını şuradan oluşturulan türler için arabirim eşlemesi[Ivector\<T >](https://go.microsoft.com/fwlink/p/?LinkId=251132)arabirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Winmdexp.exe Hata İletileri](../../../docs/framework/tools/winmdexp-exe-error-messages.md)
- [Derleme, dağıtım ve yapılandırma araçları (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
