---
title: Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0664a68d258380fd9e4824b80f0d7a244cb61e85
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894784"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)
Windows Çalışma Zamanı meta veri verme aracı (WinMDExp. exe), bir .NET Framework modülünü Windows Çalışma Zamanı meta verilerini içeren bir dosyaya dönüştürür. .NET Framework derlemeleri ve Windows Çalışma Zamanı meta veri dosyaları aynı fiziksel biçimi kullanmasına karşın, meta veri tablolarının içeriğinde farklılıklar vardır. Bu, .NET Framework derlemelerin Windows Çalışma Zamanı bileşenleri olarak otomatik olarak kullanılamayacağı anlamına gelir. . .NET Framework modülünü Windows Çalışma Zamanı bir bileşene açma işlemi, *dışarı aktarma*olarak adlandırılır. .NET Framework 4,5 ve .NET Framework 4.5.1, elde edilen Windows meta verileri (. winmd) dosyası hem meta verileri hem de uygulamayı içerir.  
  
 İçin C# **Windows Mağazası** ve Visual Studio 2013 ya da Visual Studio 2012 Visual Basic altında bulunan **Windows çalışma zamanı bileşen** şablonunu kullandığınızda, derleyici hedefi bir. winmdobj dosyası ve sonraki bir yapı adım çağrıdır WinMDExp. exe. winmdobj dosyasını bir. winmd dosyasına dışarı aktarmak için. Bu, bir Windows Çalışma Zamanı bileşeni oluşturmak için önerilen yoldur. Oluşturma süreci üzerinde, Visual Studio'nun sağladığından daha fazla kontrol sahibi olmak istediğinizde doğrudan Winmdexp.exe'yi kullanın.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız değişken veya seçenek|Açıklama|  
|------------------------|-----------------|  
|`winmdmodule`|Dışarı aktarılacak modülü (.winmdobj) belirtir. Yalnızca tek bir modüle izin verilir. Bu modülü oluşturmak için, `/target` `winmdobj` hedefle birlikte derleyici seçeneğini kullanın. Bkz. [/target: winmdobjC# (derleyici seçenekleri)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) veya [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:``docfile`<br /><br /> `/d:``docfile`|Winmdexp.exe'nin üreteceği çıktı XML belgesi dosyasını belirtir. .NET Framework 4,5 ' de, çıkış dosyası aslında giriş XML belge dosyası ile aynıdır.|  
|`/moduledoc:``docfile`<br /><br /> `/md:``docfile`|Derleyicinin ürettiği `winmdmodule`XML belge dosyasının adını belirtir.|  
|`/modulepdb:``symbolfile`<br /><br /> `/mp:``symbolfile`|Sembolleri içeren program veritabanı (PDB) dosyasının adını belirtir `winmdmodule`.|  
|`/nowarn:``warning`|Belirtilen uyarı sayısını gizler. *Uyarı*için, yalnızca hata kodunun sayısal kısmını, önünde sıfır olmadan sağlayın.|  
|`/out:``file`<br /><br /> `/o:``file`|Windows meta veri (.winmd) çıktı dosyasının adını belirtir.|  
|`/pdb:``symbolfile`<br /><br /> `/p:``symbolfile`|Dışarı aktarılan Windows meta veri (.winmd) dosyası için sembolleri içeren çıktı program veritabanı (PDB) dosyasının adını belirtir.|  
|`/reference:``winmd`<br /><br /> `/r:``winmd`|Dışarı aktarma sırasında başvurulacak bir meta veri dosyasını (.winmd veya derleme) belirtir. "\Program Files (x86) \Reference derlemelies\microsoft\framework\\içindeki başvuru derlemelerini kullanıyorsanız. NETCore\v4.5 "(" \Program Files\\... " 32 bit bilgisayarlarda), hem System. Runtime. dll hem de mscorlib. dll başvurularını ekleyin.|  
|`/utf8output`|Çıktı iletilerinde UTF-8 kodlamasının kullanılması gerektiğini belirtir.|  
|`/warnaserror+`|Tüm uyarıların hata sayılması gerektiğini belirtir.|  
|**@** `responsefile`|Seçenekleri (ve isteğe bağlı olarak `winmdmodule`) içeren bir yanıt (. rsp) dosyasını belirtir. İçindeki `responsefile` her satır tek bir bağımsız değişken veya seçenek içermelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Winmdexp.exe, rasgele bir .NET Framework derlemesini .winmd dosyasına dönüştürmek için tasarlanmamıştır. `/target:winmdobj` Seçeneğiyle derlenen bir modül gerektirir ve ek kısıtlamalar uygulanır. Bu kısıtlamaların en önemlileri, derlemenin API yüzeyi içinde gösterilen tüm türlerin Windows Çalışma Zamanı türde olması gerekir. Daha fazla bilgi için Windows Geliştirme Merkezi 'nde [ve Visual Basic ' de C# Windows çalışma zamanı bileşenleri oluşturma](https://go.microsoft.com/fwlink/p/?LinkID=238313) konusunun "Windows Çalışma Zamanı bileşenlerinde tür bildirme" bölümüne bakın.  
  
 Ya da Visual Basic sahip [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] C# bir uygulama veya Windows çalışma zamanı bileşen yazdığınızda .NET Framework, Windows çalışma zamanı daha doğal programlama yapmak için destek sağlar. Bu, [Windows Mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)makalesinde açıklanmaktadır. İşlemde, bazı yaygın olarak kullanılan Windows Çalışma Zamanı türleri .NET Framework türlerine eşlenir. WinMDExp. exe bu işlemi tersine çevirir ve karşılık gelen Windows Çalışma Zamanı türlerini kullanan bir API yüzeyi üretir. Örneğin, <xref:System.Collections.Generic.IList%601> arabiriminden oluşturulan türler Windows çalışma zamanı[\<IVector T >](https://go.microsoft.com/fwlink/p/?LinkId=251132)arabiriminden oluşturulan türlere eşlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Ve Visual Basic içinde C# Windows çalışma zamanı bileşenleri oluşturma](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Winmdexp.exe Hata İletileri](../../../docs/framework/tools/winmdexp-exe-error-messages.md)
- [Derleme, dağıtım ve Yapılandırma Araçları (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
