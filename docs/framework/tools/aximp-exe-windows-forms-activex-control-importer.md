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
ms.openlocfilehash: 6d58d1df81780c3033eab7c1ac3e860adeb374b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180422"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)
ActiveX Denetimi Alma Programı, ActiveX denetimi için bir COM tür kitaplığındaki tür tanımlarını bir Windows Formları denetimine dönüştürür.  
  
 Windows Formları yalnızca Windows Forms denetimlerini <xref:System.Windows.Forms.Control>barındırabilir — yani. Aximp.exe, Windows Formu üzerinde barındırılabilen bir ActiveX denetimi için bir sarmalayıcı sınıfı oluşturur. Bu, diğer Windows Formları denetimleri için geçerli olanla aynı tasarım zamanı desteği ve programlama metodolojisini kullanmanıza olanak tanır.  
  
 ActiveX denetimini barındırmak için, 'den <xref:System.Windows.Forms.AxHost>türetilen bir sarmalayıcı denetimi oluşturmanız gerekir. Bu sarmalayıcı denetimi, arka plandaki ActiveX denetiminin bir örneğini içerir. ActiveX denetimiyle nasıl iletişim kuracağını bilir, fakat bir Windows Formları denetimi olarak görünür. Üretilen bu denetim ActiveX denetimini barındırır ve özelliklerini, yöntemlerini ve olaylarını üretilen denetiminkiler gibi sergiler.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Açıklamalar  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*Dosya*|Dönüştürülecek ActiveX denetimini içeren kaynak dosyanın adı. Dosya bağımsız değişkeni, .dll veya .ocx uzantısına sahip olmalıdır.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/delaysign`|Sonuç olarak oluşan denetimi gecikmeli imzalamayı kullanarak imzalamasını Aximp.exe'ye belirtir. Bu seçeneği `/keycontainer:`, , `/keyfile:`veya `/publickey:` seçenek ile belirtmeniz gerekir. Gecikmiş imzalama işlemi hakkında daha fazla bilgi için, [Bir Meclis'i İmzalamayı Geciktirme'ye](../../standard/assembly/delay-sign.md)bakın.|  
|`/help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/keycontainer:`*containerName*|ContainerName tarafından belirtilen anahtar kapsayıcıda bulunan ortak/özel anahtar çiftini *containerName*kullanarak elde edilen denetimi güçlü bir adla imzalar.|  
|`/keyfile:` *filename*|Sonuç denetimini, *yayımcının dosya adında*bulunan resmi ortak/özel anahtar çiftini kullanarak güçlü bir adla imzalar.|  
|`/nologo`|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|`/out:` *filename*|Oluşturulacak derlemenin adını belirtir.|  
|`/publickey:` *filename*|*Dosya adı*ile belirtilen dosyada bulunan ortak anahtarı kullanarak ortaya çıkan denetimi güçlü bir adla işaretler.|  
|`/rcw:` *filename*|Yeni birini üretmek yerine, belirtilen çalışma zamanı çağrılabilir sarmalayıcısını kullanır. Birden çok örnek belirtebilirsiniz. Geçerli dizin, göreli yollar için kullanılır. Daha fazla bilgi için [Runtime Çağrılanabilir Sarıcı'ya](../../standard/native-interop/runtime-callable-wrapper.md)bakın.|  
|`/silent`|Başarı iletilerinin görüntülenmesini bastırır.|  
|`/source`|Windows Formları sarmalayıcısı için C# kaynak kodu üretir.|  
|`/verbose`|Ayrıntılı modu belirtir; ek ilerleme bilgilerini görüntüler.|  
|`/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
 Aximp.exe, tüm bir ActiveX Denetimi tür kitaplığını bir kerede dönüştürür ve özgün tür kitaplığında tanımlanan türler için ortak dil çalışma zamanı meta verilerini içeren ve uygulamayı denetleyen bir derleme kümesi üretir. Üretilen dosyalar aşağıdaki modele göre adlandırılır:  
  
 COM türleri için ortak dil çalışma zamanı proxy: *progid*.dll  
  
 ActiveX denetimleri için Windows Forms proxy (Ax ActiveX'i belirtir): Ax*progid*.dll  
  
> [!NOTE]
> ActiveX denetiminin bir üyesinin adı .NET Framework'te tanımlanan bir adla eşleşirse, AxHost türetilmiş sınıfını oluşturduğunda, Aximp.exe ada "Ctl" önekini ekler. Örneğin, ActiveX denetiminizin "Layout" adlı bir üyesi varsa, Layout olayı .NET Framework içinde tanımlandığından, AxHost türetilen sınıfında "CtlLayout" olarak yeniden adlandırılır.  
  
 Bu oluşturulan dosyaları [Ildasm.exe (IL Desassembler)](ildasm-exe-il-disassembler.md)gibi araçlarla inceleyebilirsiniz.  
  
 ActiveX WebBrowser denetimi (shdocvw.dll) için bir .NET derlemesi üretmek üzere Aximp.exe'yi kullanmak desteklenmez.  
  
 Aximp.exe'yi shdocvw.dll üzerinden çalıştırdığınızda, aracın çalıştığı dizinde her zaman shdocvw.dll adlı başka bir dosya oluşturur. Üretilen bu dosya Documents and Settings dizinine yerleştirilirse, Microsoft Internet Explorer ve Windows Gezgini için sorunlara neden olur. Bilgisayar yeniden başlatıldığında, Windows, shdocvw.dll'in bir kopyasını bulmak için system32 dizininden önce Documents and Settings dizinine bakar. Documents and Settings dizininde bulduğu kopyayı kullanır ve yönetilen sarmalayıcıları yüklemeyi dener. System32 dizininde bulunan shdocvw.dll sürümündeki oluşturma altyapısına dayalı olduklarından, Internet Explorer ve Windows Gezgini doğru şekilde çalışmaz. Bu sorun oluşursa, Documents and Settings dizinindeki shdocvw.dll kopyasını silin ve bilgisayarı yeniden başlatın.  
  
 Uygulama geliştirmede kullanmak üzere bir .NET derlemesi oluşturmak için Aximp.exe'yi shdocvw.dll ile birlikte kullanmak da sorunlara neden olabilir. Bu durumda, uygulamanız shdocvw.dll'in hem sistem sürümünü hem de üretilen sürümünü yükler ve istem sürümüne öncelik verebilir. Bu durumda, WebBrowser ActiveX denetimi içinde bir Web sayfasını yüklemeyi denediğinizde, kullanıcılara bir Aç/Kaydet iletişim kutusu görüntülenebilir. Kullanıcı **Aç'ı**tıklattığında, Web sayfası Internet Explorer'da açılır. Bu yalnızca, Internet Explorer sürüm 6 veya önceki sürümlerin çalıştığı bilgisayarlarda olur. Bu sorunu önlemek için <xref:System.Windows.Forms.WebBrowser> yönetilen denetimi kullanın veya Yönetilen shdocvw.dll'yi oluşturmak için Visual Studio'yu [kullanın.](../interop/how-to-add-references-to-type-libraries.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut Media Player kontrolü `msdxm.ocx`için MediaPlayer.dll ve AxMediaPlayer.dll oluşturur.  
  
```console
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Ildasm.exe (IL Ayrıştırıcı)](ildasm-exe-il-disassembler.md)
