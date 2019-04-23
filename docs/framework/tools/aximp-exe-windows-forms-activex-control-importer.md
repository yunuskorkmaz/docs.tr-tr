---
title: Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b7e9401cbd26c62f88ccb4a4b8c2caeb78768d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119203"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)
ActiveX Denetimi Alma Programı, ActiveX denetimi için bir COM tür kitaplığındaki tür tanımlarını bir Windows Formları denetimine dönüştürür.  
  
 Windows Formları yalnızca Windows Forms denetimleri ana — diğer bir deyişle, türetilmiş sınıflar <xref:System.Windows.Forms.Control>. Aximp.exe, Windows Formu üzerinde barındırılabilen bir ActiveX denetimi için bir sarmalayıcı sınıfı oluşturur. Bu, diğer Windows Formları denetimleri için geçerli olanla aynı tasarım zamanı desteği ve programlama metodolojisini kullanmanıza olanak tanır.  
  
 ActiveX denetimini barındırmak için türetilen bir sarmalayıcı denetimi üretmeniz <xref:System.Windows.Forms.AxHost>. Bu sarmalayıcı denetimi, arka plandaki ActiveX denetiminin bir örneğini içerir. ActiveX denetimiyle nasıl iletişim kuracağını bilir, fakat bir Windows Formları denetimi olarak görünür. Üretilen bu denetim ActiveX denetimini barındırır ve özelliklerini, yöntemlerini ve olaylarını üretilen denetiminkiler gibi sergiler.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Açıklamalar  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*Dosya*|Dönüştürülecek ActiveX denetimini içeren kaynak dosyanın adı. Dosya bağımsız değişkeni, .dll veya .ocx uzantısına sahip olmalıdır.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/delaysign`|Sonuç olarak oluşan denetimi gecikmeli imzalamayı kullanarak imzalamasını Aximp.exe'ye belirtir. Bu seçeneği ile birlikte belirtmelisiniz `/keycontainer:`, `/keyfile:`, veya `/publickey:` seçeneği. Gecikmeli imzalama işlemi hakkında daha fazla bilgi için bkz. [derlemeyi imzalamayı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).|  
|`/help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/keycontainer:` *kapsayıcı adı*|Sonuç olarak oluşan denetimi tarafından belirtilen anahtar kapsayıcısında bulunan ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar *containerName*.|  
|`/keyfile:` *Dosya adı*|Sonuç olarak oluşan denetimi bulunan yayımcının resmi ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar *filename*.|  
|`/nologo`|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|`/out:` *Dosya adı*|Oluşturulacak derlemenin adını belirtir.|  
|`/publickey:` *Dosya adı*|Sonuç olarak oluşan denetimi tarafından belirtilen dosyada bulunan genel anahtarı kullanarak tanımlayıcı bir adla imzalar *filename*.|  
|`/rcw:` *Dosya adı*|Yeni birini üretmek yerine, belirtilen çalışma zamanı çağrılabilir sarmalayıcısını kullanır. Birden çok örnek belirtebilirsiniz. Geçerli dizin, göreli yollar için kullanılır. Daha fazla bilgi için [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md).|  
|`/silent`|Başarı iletilerinin görüntülenmesini bastırır.|  
|`/source`|Windows Formları sarmalayıcısı için C# kaynak kodu üretir.|  
|`/verbose`|Ayrıntılı modu belirtir; ek ilerleme bilgilerini görüntüler.|  
|`/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
 Aximp.exe, tüm bir ActiveX Denetimi tür kitaplığını bir kerede dönüştürür ve özgün tür kitaplığında tanımlanan türler için ortak dil çalışma zamanı meta verilerini içeren ve uygulamayı denetleyen bir derleme kümesi üretir. Üretilen dosyalar aşağıdaki modele göre adlandırılır:  
  
 COM türleri için ortak dil çalışma zamanı proxy'si: *ProgID*.dll  
  
 Windows Formları Proxy'si (burada Ax ActiveX gösterir) ActiveX denetimleri için: AX*ProgID*.dll  
  
> [!NOTE]
>  ActiveX denetiminin bir üyesinin adı .NET Framework'te tanımlanan bir adla eşleşirse, AxHost türetilmiş sınıfını oluşturduğunda, Aximp.exe ada "Ctl" önekini ekler. Örneğin, ActiveX denetiminizin "Layout" adlı bir üyesi varsa, Layout olayı .NET Framework içinde tanımlandığından, AxHost türetilen sınıfında "CtlLayout" olarak yeniden adlandırılır.  
  
 Üretilen bu dosyaları araçlarla gibi inceleyebilirsiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
 ActiveX WebBrowser denetimi (shdocvw.dll) için bir .NET derlemesi üretmek üzere Aximp.exe'yi kullanmak desteklenmez.  
  
 Aximp.exe'yi shdocvw.dll üzerinden çalıştırdığınızda, aracın çalıştığı dizinde her zaman shdocvw.dll adlı başka bir dosya oluşturur. Üretilen bu dosya Documents and Settings dizinine yerleştirilirse, Microsoft Internet Explorer ve Windows Gezgini için sorunlara neden olur. Bilgisayar yeniden başlatıldığında, Windows, shdocvw.dll'in bir kopyasını bulmak için system32 dizininden önce Documents and Settings dizinine bakar. Documents and Settings dizininde bulduğu kopyayı kullanır ve yönetilen sarmalayıcıları yüklemeyi dener. System32 dizininde bulunan shdocvw.dll sürümündeki oluşturma altyapısına dayalı olduklarından, Internet Explorer ve Windows Gezgini doğru şekilde çalışmaz. Bu sorun oluşursa, Documents and Settings dizinindeki shdocvw.dll kopyasını silin ve bilgisayarı yeniden başlatın.  
  
 Uygulama geliştirmede kullanmak üzere bir .NET derlemesi oluşturmak için Aximp.exe'yi shdocvw.dll ile birlikte kullanmak da sorunlara neden olabilir. Bu durumda, uygulamanız shdocvw.dll'in hem sistem sürümünü hem de üretilen sürümünü yükler ve istem sürümüne öncelik verebilir. Bu durumda, WebBrowser ActiveX denetimi içinde bir Web sayfasını yüklemeyi denediğinizde, kullanıcılara bir Aç/Kaydet iletişim kutusu görüntülenebilir. Kullanıcı tıkladığında **açık**, Web sayfası Internet Explorer'da açılır. Bu yalnızca, Internet Explorer sürüm 6 veya önceki sürümlerin çalıştığı bilgisayarlarda olur. Bu sorunu önlemek için yönetilen kullanın <xref:System.Windows.Forms.WebBrowser> açıklandığı gibi yönetilen shdocvw.dll üretmek için Visual Studio'yu kullanın veya Denetim [nasıl yapılır: Tür kitaplıklarına başvurular ekleme](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut Media Player denetimi için MediaPlayer.dll ve AxMediaPlayer.dll üretir `msdxm.ocx`.  
  
```  
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Ildasm.exe (IL Ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
