---
title: Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a228513bd29e35e8793124846de16f1c8bf4c10
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208536"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] Meta verileri dışarı aktarma Aracı (Winmdexp.exe) bir .NET Framework modülünü içeren bir dosyaya dönüştürür [!INCLUDE[wrt](../../../includes/wrt-md.md)] meta verileri. Ancak .NET Framework derlemeleri ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] meta veri dosyaları aynı fiziksel biçim kullanın, .NET Framework derlemeleri otomatik olarak kullanılamaz, yani meta veri tablolarının içeriğinde farklar vardır [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri . Bir .NET Framework modülünü işleminin bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni olarak adlandırılır *verme*. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], sonuçta elde edilen Windows meta veri (.winmd) dosyası hem meta veriler hem de uygulama bulunur.  
  
 Kullanırken  **[!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşen** altında bulunan şablon **Windows Store** C# ve Visual Basic'te [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] veya [!INCLUDE[vs_dev11_ext](../../../includes/vs-dev11-ext-md.md)], derleyici hedefi bir .winmdobj dosyası olduğu ve sonraki Oluşturma adımı .winmdobj dosyasını bir .winmd dosyasına aktarmak için Winmdexp.exe'yi çağırır. Derleme için önerilen yöntem budur bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni. Oluşturma süreci üzerinde, Visual Studio'nun sağladığından daha fazla kontrol sahibi olmak istediğinizde doğrudan Winmdexp.exe'yi kullanın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
winmdexp [options] winmdmodule  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız değişken veya seçenek|Açıklama|  
|------------------------|-----------------|  
|`winmdmodule`|Dışarı aktarılacak modülü (.winmdobj) belirtir. Yalnızca tek bir modüle izin verilir. Bu modülü oluşturmak için kullanın `/target` derleyici seçeneğiyle `winmdobj` hedef. Bkz: [/target: winmdobj (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) veya [/target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Winmdexp.exe'nin üreteceği çıktı XML belgesi dosyasını belirtir. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], çıktı dosyası temelde girdi XML belgeleme dosyasıyla aynıdır.|  
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
 Winmdexp.exe, rasgele bir .NET Framework derlemesini .winmd dosyasına dönüştürmek için tasarlanmamıştır. İle derlenmiş bir modül gerektirir `/target:winmdobj` seçeneği ve ek kısıtlamalar uygulanır. Bu kısıtlamaların en önemlisi derlemenin API yüzeyinde sunulan tüm türleri olması gerekliliğidir [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri. Daha fazla bilgi için makalenin "Windows çalışma zamanı bileşenleri türleri bildirme" bölümüne bakın. [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](https://go.microsoft.com/fwlink/p/?LinkID=238313) Windows geliştirme Merkezi'nde.  
  
 Yazdığınızda bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama veya [!INCLUDE[wrt](../../../includes/wrt-md.md)] C# veya Visual Basic ile bileşen, .NET Framework ile programlama hale getirmek için destek sağlar [!INCLUDE[wrt](../../../includes/wrt-md.md)] daha doğal. Bu makalede açıklanan [Windows Store uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). İşlemde, sık kullanılan bazı [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri .NET Framework türleri ile eşleştirilir. Winmdexp.exe bu işlemi tersine çevirir ve karşılık gelen kullanan bir API yüzey oluşturur [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri. Örneğin, oluşturulan türler <xref:System.Collections.Generic.IList%601> oluşturulan türler için arabirim eşlemesi [!INCLUDE[wrt](../../../includes/wrt-md.md)] [Ivector\<T >](https://go.microsoft.com/fwlink/p/?LinkId=251132)arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](https://go.microsoft.com/fwlink/p/?LinkID=238313)  
 [Winmdexp.exe Hata İletileri](../../../docs/framework/tools/winmdexp-exe-error-messages.md)  
 [Derleme, dağıtım ve yapılandırma araçları (.NET Framework)](https://msdn.microsoft.com/library/b8c921be-6012-4181-b8d4-ab15813fc9a7)
