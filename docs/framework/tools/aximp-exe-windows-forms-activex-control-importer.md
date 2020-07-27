---
title: Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)
description: Windows Forms ActiveX denetim Içeri aktarıcı Aximp.exe anlayın. Bu araç, ActiveX için bir COM tür kitaplığındaki tür tanımlarını Windows Forms olarak dönüştürür.
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
ms.openlocfilehash: d4fd6762195078963b43392178996a61f90feb94
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167341"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)
ActiveX Denetimi Alma Programı, ActiveX denetimi için bir COM tür kitaplığındaki tür tanımlarını bir Windows Formları denetimine dönüştürür.  
  
 Windows Forms, yalnızca Windows Forms denetimleri barındırabilir — diğer bir deyişle, öğesinden türetilmiş sınıflar <xref:System.Windows.Forms.Control> . Aximp.exe, Windows Formu üzerinde barındırılabilen bir ActiveX denetimi için bir sarmalayıcı sınıfı oluşturur. Bu, diğer Windows Formları denetimleri için geçerli olanla aynı tasarım zamanı desteği ve programlama metodolojisini kullanmanıza olanak tanır.  
  
 ActiveX denetimini barındırmak için, öğesinden türetilen bir sarmalayıcı denetimi oluşturmanız gerekir <xref:System.Windows.Forms.AxHost> . Bu sarmalayıcı denetimi, arka plandaki ActiveX denetiminin bir örneğini içerir. ActiveX denetimiyle nasıl iletişim kuracağını bilir, fakat bir Windows Formları denetimi olarak görünür. Üretilen bu denetim ActiveX denetimini barındırır ve özelliklerini, yöntemlerini ve olaylarını üretilen denetiminkiler gibi sergiler.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Açıklamalar  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*dosyasýný*|Dönüştürülecek ActiveX denetimini içeren kaynak dosyanın adı. Dosya bağımsız değişkeni, .dll veya .ocx uzantısına sahip olmalıdır.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/delaysign`|Sonuç olarak oluşan denetimi gecikmeli imzalamayı kullanarak imzalamasını Aximp.exe'ye belirtir. Bu seçeneği,, ya da seçeneğiyle belirtmeniz `/keycontainer:` gerekir `/keyfile:` `/publickey:` . Gecikmeli imzalama işlemi hakkında daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../standard/assembly/delay-sign.md).|  
|`/help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/keycontainer:`*ContainerName*|Sonuç denetimini, *ContainerName*tarafından belirtilen anahtar kapsayıcısında bulunan ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.|  
|`/keyfile:` *filename*|Ortaya çıkan denetimi, yayımcının *dosya adında*bulunan resmi ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.|  
|`/nologo`|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|`/out:` *filename*|Oluşturulacak derlemenin adını belirtir.|  
|`/publickey:` *filename*|Elde edilen denetimi dosya *adı*tarafından belirtilen dosyada bulunan ortak anahtarı kullanarak tanımlayıcı bir adla imzalar.|  
|`/rcw:` *filename*|Yeni birini üretmek yerine, belirtilen çalışma zamanı çağrılabilir sarmalayıcısını kullanır. Birden çok örnek belirtebilirsiniz. Geçerli dizin, göreli yollar için kullanılır. Daha fazla bilgi için bkz. [çalışma zamanında çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md).|  
|`/silent`|Başarı iletilerinin görüntülenmesini bastırır.|  
|`/source`|Windows Formları sarmalayıcısı için C# kaynak kodu üretir.|  
|`/verbose`|Ayrıntılı modu belirtir; ek ilerleme bilgilerini görüntüler.|  
|`/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
 Aximp.exe, tüm bir ActiveX Denetimi tür kitaplığını bir kerede dönüştürür ve özgün tür kitaplığında tanımlanan türler için ortak dil çalışma zamanı meta verilerini içeren ve uygulamayı denetleyen bir derleme kümesi üretir. Üretilen dosyalar aşağıdaki modele göre adlandırılır:  
  
 COM türleri için ortak dil çalışma zamanı proxy 'si: *ProgID*. dll  
  
 ActiveX denetimleri için proxy Windows Forms (AX 'in ActiveX 'i belirtir): AX*ProgID*. dll  
  
> [!NOTE]
> ActiveX denetiminin bir üyesinin adı .NET Framework'te tanımlanan bir adla eşleşirse, AxHost türetilmiş sınıfını oluşturduğunda, Aximp.exe ada "Ctl" önekini ekler. Örneğin, ActiveX denetiminizin "Layout" adlı bir üyesi varsa, Layout olayı .NET Framework içinde tanımlandığından, AxHost türetilen sınıfında "CtlLayout" olarak yeniden adlandırılır.  
  
 Bu oluşturulan dosyaları [Ildasm.exe (Il ayırıcı)](ildasm-exe-il-disassembler.md)gibi araçlarla inceleyebilirsiniz.  
  
 ActiveX WebBrowser denetimi (shdocvw.dll) için bir .NET derlemesi üretmek üzere Aximp.exe'yi kullanmak desteklenmez.  
  
 Aximp.exe'yi shdocvw.dll üzerinden çalıştırdığınızda, aracın çalıştığı dizinde her zaman shdocvw.dll adlı başka bir dosya oluşturur. Üretilen bu dosya Documents and Settings dizinine yerleştirilirse, Microsoft Internet Explorer ve Windows Gezgini için sorunlara neden olur. Bilgisayar yeniden başlatıldığında, Windows, shdocvw.dll'in bir kopyasını bulmak için system32 dizininden önce Documents and Settings dizinine bakar. Documents and Settings dizininde bulduğu kopyayı kullanır ve yönetilen sarmalayıcıları yüklemeyi dener. System32 dizininde bulunan shdocvw.dll sürümündeki oluşturma altyapısına dayalı olduklarından, Internet Explorer ve Windows Gezgini doğru şekilde çalışmaz. Bu sorun oluşursa, Documents and Settings dizinindeki shdocvw.dll kopyasını silin ve bilgisayarı yeniden başlatın.  
  
 Uygulama geliştirmede kullanmak üzere bir .NET derlemesi oluşturmak için Aximp.exe'yi shdocvw.dll ile birlikte kullanmak da sorunlara neden olabilir. Bu durumda, uygulamanız shdocvw.dll'in hem sistem sürümünü hem de üretilen sürümünü yükler ve istem sürümüne öncelik verebilir. Bu durumda, WebBrowser ActiveX denetimi içinde bir Web sayfasını yüklemeyi denediğinizde, kullanıcılara bir Aç/Kaydet iletişim kutusu görüntülenebilir. Kullanıcı **Aç**' ı tıklattığında, Web sayfası Internet Explorer 'da açılır. Bu yalnızca, Internet Explorer sürüm 6 veya önceki sürümlerin çalıştığı bilgisayarlarda olur. Bu sorunu engellemek için yönetilen <xref:System.Windows.Forms.WebBrowser> denetimi kullanın veya Visual Studio 'yu kullanarak yönetilen shdocvw.dll oluşturma bölümünde açıklandığı gibi, bkz. [tür kitaplıklarına başvurular ekleme](../interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut Media Player denetimi için MediaPlayer.dll ve AxMediaPlayer.dll oluşturur `msdxm.ocx` .  
  
```console
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Ildasm.exe (Il ayırıcı)](ildasm-exe-il-disassembler.md)
