---
title: Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: 52820b78f6ed7b02e80df66f90a01143b31d9b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447283"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
Windows Çalışma Zamanı meta veri verme aracı (WinMDExp. exe), bir .NET Framework modülünü Windows Çalışma Zamanı meta verilerini içeren bir dosyaya dönüştürür. .NET Framework derlemeleri ve Windows Çalışma Zamanı meta veri dosyaları aynı fiziksel biçimi kullanmasına karşın, meta veri tablolarının içeriğinde farklılıklar vardır. Bu, .NET Framework derlemelerin Windows Çalışma Zamanı bileşenleri olarak otomatik olarak kullanılamayacağı anlamına gelir. . .NET Framework modülünü Windows Çalışma Zamanı bir bileşene açma işlemi, *dışarı aktarma*olarak adlandırılır. .NET Framework 4,5 ve .NET Framework 4.5.1, elde edilen Windows meta verileri (. winmd) dosyası hem meta verileri hem de uygulamayı içerir.  
  
 **Windows Mağazası** 'nın altında bulunan C# ve Visual Studio 2013 ya da Visual Studio 2012 ' de Visual Basic bulunan **Windows çalışma zamanı bileşen** şablonunu kullandığınızda, derleyici hedefi bir. winmdobj dosyasıdır ve sonraki derleme adımı. winmdobj dosyasını bir. winmd dosyasına aktarmak için WinMDExp. exe ' yi çağırır. Bu, bir Windows Çalışma Zamanı bileşeni oluşturmak için önerilen yoldur. Oluşturma süreci üzerinde, Visual Studio'nun sağladığından daha fazla kontrol sahibi olmak istediğinizde doğrudan Winmdexp.exe'yi kullanın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız değişken veya seçenek|Açıklama|  
|------------------------|-----------------|  
|`winmdmodule`|Dışarı aktarılacak modülü (.winmdobj) belirtir. Yalnızca tek bir modüle izin verilir. Bu modülü oluşturmak için `winmdobj` hedefle birlikte `/target` derleyici seçeneğini kullanın. Bkz: [-target: winmdobjC# (derleyici seçenekleri)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) veya [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Winmdexp.exe'nin üreteceği çıktı XML belgesi dosyasını belirtir. .NET Framework 4,5 ' de, çıkış dosyası aslında giriş XML belge dosyası ile aynıdır.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Derleyicinin `winmdmodule`ile ürettiği XML belge dosyasının adını belirtir.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|`winmdmodule`sembolleri içeren program veritabanı (PDB) dosyasının adını belirtir.|  
|`/nowarn:``warning`|Belirtilen uyarı sayısını gizler. *Uyarı*için, yalnızca hata kodunun sayısal kısmını, önünde sıfır olmadan sağlayın.|  
|`/out:``file`<br /><br /> `/o:``file`|Windows meta veri (.winmd) çıktı dosyasının adını belirtir.|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Dışarı aktarılan Windows meta veri (.winmd) dosyası için sembolleri içeren çıktı program veritabanı (PDB) dosyasının adını belirtir.|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Dışarı aktarma sırasında başvurulacak bir meta veri dosyasını (.winmd veya derleme) belirtir. "\Program Files (x86) \Reference derlemelies\microsoft\framework\\içinde başvuru derlemelerini kullanıyorsanız. NETCore\v4.5 "(" \Program Files\\... " 32 bit bilgisayarlarda), hem System. Runtime. dll hem de mscorlib. dll başvurularını ekleyin.|  
|`/utf8output`|Çıktı iletilerinde UTF-8 kodlamasının kullanılması gerektiğini belirtir.|  
|`/warnaserror+`|Tüm uyarıların hata sayılması gerektiğini belirtir.|  
|**@** `responsefile`|Seçenekleri (ve isteğe bağlı olarak `winmdmodule`) içeren bir yanıt (. rsp) dosyasını belirtir. `responsefile` her satır tek bir bağımsız değişken veya seçenek içermelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Winmdexp.exe, rasgele bir .NET Framework derlemesini .winmd dosyasına dönüştürmek için tasarlanmamıştır. `/target:winmdobj` seçeneği ile derlenen bir modül gerektirir ve ek kısıtlamalar uygulanır. Bu kısıtlamaların en önemlileri, derlemenin API yüzeyi içinde gösterilen tüm türlerin Windows Çalışma Zamanı türde olması gerekir. Daha fazla bilgi için, [ C# ve Visual Basic Windows çalışma zamanı bileşenleri oluşturma](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))makalesinin "Windows Çalışma Zamanı bileşenlerinde tür bildirme" bölümüne bakın.
  
 Ya da Visual Basic sahip C# bir Windows 8. x Mağazası uygulaması veya Windows çalışma zamanı bileşeni yazdığınızda .NET Framework, Windows çalışma zamanı daha doğal programlama yapmak için destek sağlar. Bu, [Windows Mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)makalesinde açıklanmaktadır. İşlemde, bazı yaygın olarak kullanılan Windows Çalışma Zamanı türleri .NET Framework türlerine eşlenir. WinMDExp. exe bu işlemi tersine çevirir ve karşılık gelen Windows Çalışma Zamanı türlerini kullanan bir API yüzeyi üretir. Örneğin, <xref:System.Collections.Generic.IList%601> arabiriminden oluşturulan türler, Windows Çalışma Zamanı <xref:Windows.Foundation.Collections.IVector%601> arabiriminden oluşturulan türlere eşlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Ve Visual Basic içinde C# Windows çalışma zamanı bileşenleri oluşturma](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))
- [Winmdexp.exe Hata İletileri](winmdexp-exe-error-messages.md)
- [Derleme, dağıtım ve Yapılandırma Araçları (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
