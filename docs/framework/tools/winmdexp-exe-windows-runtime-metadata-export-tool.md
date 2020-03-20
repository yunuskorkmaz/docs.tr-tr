---
title: Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: 52820b78f6ed7b02e80df66f90a01143b31d9b29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74447283"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
Windows Runtime Meta data Export Tool (Winmdexp.exe), .NET Framework modüllerini Windows Runtime meta verilerini içeren bir dosyaya dönüştürür. .NET Framework derlemeleri ve Windows Runtime meta veri dosyaları aynı fiziksel biçimi kullansa da, meta veri tablolarının içeriğinde farklılıklar vardır, bu da .NET Framework derlemelerinin Windows Runtime Bileşenleri olarak otomatik olarak kullanılabilir olmadığı anlamına gelir . Bir .NET Framework modülünün Windows Runtime bileşenine dönüştürülmesi işlemine *dışa aktarma*denir. .NET Framework 4.5 ve .NET Framework 4.5.1'de, ortaya çıkan Windows meta verileri (.winmd) dosyası hem meta verileri hem de uygulamayı içerir.  
  
 Visual Studio 2013 veya Visual Studio 2012'de **C#** ve Visual Basic için Windows Mağazası altında bulunan **Windows Runtime Bileşeni** şablonu kullandığınızda, derleyici hedefi bir .winmdobj dosyasıdır ve sonraki bir yapı adımı .winmdobj dosyasını .winmddosyaya aktarmak için Winmdexp.exe'yi çağırır. Bu, windows runtime bileşeni oluşturmak için önerilen yoldur. Oluşturma süreci üzerinde, Visual Studio'nun sağladığından daha fazla kontrol sahibi olmak istediğinizde doğrudan Winmdexp.exe'yi kullanın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız değişken veya seçenek|Açıklama|  
|------------------------|-----------------|  
|`winmdmodule`|Dışarı aktarılacak modülü (.winmdobj) belirtir. Yalnızca tek bir modüle izin verilir. Bu modülü oluşturmak `/target` `winmdobj` için, hedefle birlikte derleyici seçeneğini kullanın. Bkz. [-hedef:winmdobj (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) veya [-hedef (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Winmdexp.exe'nin üreteceği çıktı XML belgesi dosyasını belirtir. .NET Framework 4.5'te, çıktı dosyası aslında xml belgeleme dosyası girişiyle aynıdır.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Derleyicinin ürettiği XML dokümantasyon dosyasının adını `winmdmodule`belirtir.|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Için semboller içeren program veritabanı (PDB) dosyasının `winmdmodule`adını belirtir.|  
|`/nowarn:` `warning`|Belirtilen uyarı sayısını gizler. *Uyarı*için, satır aralığı sıfırları olmadan hata kodunun yalnızca sayısal kısmını tedarik edin.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Windows meta veri (.winmd) çıktı dosyasının adını belirtir.|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Dışarı aktarılan Windows meta veri (.winmd) dosyası için sembolleri içeren çıktı program veritabanı (PDB) dosyasının adını belirtir.|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Dışarı aktarma sırasında başvurulacak bir meta veri dosyasını (.winmd veya derleme) belirtir. Başvuru derlemelerini "\Program Dosyaları (x86)\Başvuru Derlemeleri\Microsoft\Framework\\" de kullanırsanız. NETCore\v4.5" ("\Program\\Dosyaları ..." 32-bit bilgisayarlarda), hem System.Runtime.dll ve mscorlib.dll referansları içerir.|  
|`/utf8output`|Çıktı iletilerinde UTF-8 kodlamasının kullanılması gerektiğini belirtir.|  
|`/warnaserror+`|Tüm uyarıların hata sayılması gerektiğini belirtir.|  
|**@** `responsefile`|Seçenekler (ve isteğe bağlı) `winmdmodule`içeren bir yanıt (.rsp) dosyası belirtir. Her satır `responsefile` tek bir bağımsız değişken veya seçenek içermelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Winmdexp.exe, rasgele bir .NET Framework derlemesini .winmd dosyasına dönüştürmek için tasarlanmamıştır. Bu `/target:winmdobj` seçenek ile derlenmiş bir modül gerektirir ve ek kısıtlamalar geçerlidir. Bu kısıtlamaların en önemlisi, derlemenin API yüzeyinde açıkta kalan tüm türlerin Windows Runtime türleri olması gerektiğidir. Daha fazla bilgi için, [C# ve Visual Basic'te Windows Runtime Bileşenleri Oluşturma](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))makalesinin "Windows Runtime Bileşenlerinde türleri bildirme" bölümüne bakın.
  
 Bir Windows 8.x Store uygulaması veya C# veya Visual Basic içeren bir Windows Runtime bileşeni yazdığınızda,.NET Framework, Windows Runtime ile programlamayı daha doğal hale getirmek için destek sağlar. Bu makalede ele alınmıştır [.NET Framework Support Windows Mağazası Uygulamaları ve Windows Runtime için.](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md) Bu işlemde, sık kullanılan bazı Windows Runtime türleri .NET Framework türlerine eşlenir. Winmdexp.exe bu işlemi tersine çevirir ve ilgili Windows Runtime türlerini kullanan bir API yüzeyi üretir. Örneğin, arabirim eşlemi'nden <xref:System.Collections.Generic.IList%601> Windows Runtime <xref:Windows.Foundation.Collections.IVector%601> arabiriminden oluşturulmuş türlere oluşturulmuş türler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [C# ve Visual Basic'te Windows Runtime Bileşenleri Oluşturma](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))
- [Winmdexp.exe Hata İletileri](winmdexp-exe-error-messages.md)
- [Oluşturma, Dağıtım ve Yapılandırma Araçları (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
