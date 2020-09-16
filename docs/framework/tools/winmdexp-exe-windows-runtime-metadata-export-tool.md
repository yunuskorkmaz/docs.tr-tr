---
title: Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
description: Windows Çalışma Zamanı meta verileri dışarı aktarma aracı Winmdexp.exe anlayın. Bu araç, bir .NET modülünü Windows Çalışma Zamanı meta veri içeren bir dosyaya dönüştürür.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: dc36533a4f0c48e8e8a5930540746a46ba596751
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543244"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
Windows Çalışma Zamanı meta veri verme aracı (Winmdexp.exe), .NET Framework modülünü Windows Çalışma Zamanı meta verileri içeren bir dosyaya dönüştürür. .NET Framework derlemeleri ve Windows Çalışma Zamanı meta veri dosyaları aynı fiziksel biçimi kullanmasına karşın, meta veri tablolarının içeriğinde farklılıklar vardır. Bu, .NET Framework derlemelerin Windows Çalışma Zamanı bileşenleri olarak otomatik olarak kullanılamayacağı anlamına gelir. .NET Framework modülünü Windows Çalışma Zamanı bir bileşene açma işlemi, *dışarı aktarma*olarak adlandırılır. .NET Framework 4,5 ve .NET Framework 4.5.1, elde edilen Windows meta verileri (. winmd) dosyası hem meta verileri hem de uygulamayı içerir.  
  
 C# için **Windows Mağazası** ve Visual Studio 2013 ya da Visual Studio 2012 Visual Basic içinde bulunan **Windows çalışma zamanı bileşen** şablonunu kullandığınızda, derleyici hedefi bir. winmdobj dosyasıdır ve sonraki derleme adımı,. winmdobj dosyasını bir. winmd dosyasına dışarı aktarmak için Winmdexp.exe çağırır. Bu, bir Windows Çalışma Zamanı bileşeni oluşturmak için önerilen yoldur. Oluşturma süreci üzerinde, Visual Studio'nun sağladığından daha fazla kontrol sahibi olmak istediğinizde doğrudan Winmdexp.exe'yi kullanın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız değişken veya seçenek|Description|  
|------------------------|-----------------|  
|`winmdmodule`|Dışarı aktarılacak modülü (.winmdobj) belirtir. Yalnızca tek bir modüle izin verilir. Bu modülü oluşturmak için, `/target` hedefle birlikte derleyici seçeneğini kullanın `winmdobj` . Bkz: [-target: winmdobj (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) veya [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Winmdexp.exe'nin üreteceği çıktı XML belgesi dosyasını belirtir. .NET Framework 4,5 ' de, çıkış dosyası aslında giriş XML belge dosyası ile aynıdır.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Derleyicinin ürettiği XML belge dosyasının adını belirtir `winmdmodule` .|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Sembolleri içeren program veritabanı (PDB) dosyasının adını belirtir `winmdmodule` .|  
|`/nowarn:` `warning`|Belirtilen uyarı sayısını gizler. *Uyarı*için, yalnızca hata kodunun sayısal kısmını, önünde sıfır olmadan sağlayın.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Windows meta veri (.winmd) çıktı dosyasının adını belirtir.|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Dışarı aktarılan Windows meta veri (.winmd) dosyası için sembolleri içeren çıktı program veritabanı (PDB) dosyasının adını belirtir.|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Dışarı aktarma sırasında başvurulacak bir meta veri dosyasını (.winmd veya derleme) belirtir. "\Program Files (x86) \Reference derlemelies\microsoft\framework içindeki başvuru derlemelerini kullanıyorsanız \\ . NETCore\v4.5 "(" \Program Files \\ ... " 32 bit bilgisayarlarda), hem System.Runtime.dll hem de mscorlib.dll başvurularını ekleyin.|  
|`/utf8output`|Çıktı iletilerinde UTF-8 kodlamasının kullanılması gerektiğini belirtir.|  
|`/warnaserror+`|Tüm uyarıların hata sayılması gerektiğini belirtir.|  
|**@** `responsefile`|Seçenekleri (ve isteğe bağlı olarak) içeren bir yanıt (. rsp) dosyasını belirtir `winmdmodule` . İçindeki her satır `responsefile` tek bir bağımsız değişken veya seçenek içermelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Winmdexp.exe, rasgele bir .NET Framework derlemesini .winmd dosyasına dönüştürmek için tasarlanmamıştır. Seçeneğiyle derlenen bir modül gerektirir `/target:winmdobj` ve ek kısıtlamalar uygulanır. Bu kısıtlamaların en önemlileri, derlemenin API yüzeyi içinde gösterilen tüm türlerin Windows Çalışma Zamanı türde olması gerekir. Daha fazla bilgi için [C# ve Visual Basic Windows çalışma zamanı bileşenleri oluşturma](/previous-versions/br230301(v=vs.110))makalesinin "Windows Çalışma Zamanı bileşenlerinde tür bildirme" bölümüne bakın.
  
 C# veya Visual Basic sahip bir Windows 8. x mağaza uygulaması veya Windows Çalışma Zamanı bileşeni yazdığınızda .NET Framework, Windows Çalışma Zamanı daha doğal programlama yapmak için destek sağlar. Bu, [Windows Mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)makalesinde açıklanmaktadır. İşlemde, bazı yaygın olarak kullanılan Windows Çalışma Zamanı türleri .NET Framework türlerine eşlenir. Winmdexp.exe bu işlemi tersine çevirir ve karşılık gelen Windows Çalışma Zamanı türlerini kullanan bir API yüzeyi üretir. Örneğin, arabiriminden oluşturulan türler <xref:System.Collections.Generic.IList%601> Windows çalışma zamanı arabiriminden oluşturulan türlere eşlenir <xref:Windows.Foundation.Collections.IVector%601> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [C# ve Visual Basic Windows Çalışma Zamanı bileşenleri oluşturma](/previous-versions/br230301(v=vs.110))
- [Winmdexp.exe hata Iletileri](winmdexp-exe-error-messages.md)
- [Derleme, dağıtım ve Yapılandırma Araçları (.NET Framework)](/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
