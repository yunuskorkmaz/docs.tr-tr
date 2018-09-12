---
title: -errorreport (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: dcbb9467da87a82147176bb0feb00383aff2c77f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44698686"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (C# Derleyici Seçenekleri)
Bu seçenek, bir C# derleyici iç hatası Microsoft'a bildirmek için kullanışlı bir yol sağlar.  
  
> [!NOTE]
>  Windows Vista ve Windows Server 2008'de yaptığınız için Visual Studio hata raporlama ayarlarını Windows hata bildirimi (WER) aracılığıyla yapılan ayarlarını geçersiz kılmaz. WER ayarları her zaman Visual Studio hata bildirimi ayarları üzerinde önceliklidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Arguments  
 **Yok**  
 Derleyici iç hatalarıyla ilgili raporlar toplanmaz ve Microsoft'a gönderilir.  
  
 **istemi**  
 Derleyici iç hatası aldığınızda rapor göndermek isteyip istemediğinizi sorar. **İstemi** geliştirme ortamında bir uygulama derlediğinizde varsayılandır.  
  
 **Kuyruk**  
 Hata raporunu kuyruğa alır. Yönetici kimlik bilgileriyle oturum açtığında günlüğe kaydedilen son Time hatalar bildirebilir. Üç günde birden çok kez hata raporu göndermek için istenmez. **Kuyruk** , komut satırında bir uygulama derlerken varsayılandır.  
  
 **Gönder**  
 Derleyici iç hata raporlarını otomatik olarak Microsoft'a gönderir. Bu seçeneği etkinleştirmek için önce Microsoft veri toplama ilkesini kabul etmesi gerekir. Belirttiğiniz ilk kez **- errorreport: gönderme** bir bilgisayarda, bir derleyici iletisi Microsoft veri koleksiyonu ilkesini içeren Web sitesi başvuracaktır.  
    
## <a name="remarks"></a>Açıklamalar  
 Derleyici bir kaynak kodu dosyasını işlerken bir iç derleyici hatası (ICE) sonuçlanır. Bir ICE ortaya çıktığında, derleyici bir çıktı dosyasını veya kodunuzu düzeltmek için kullanabileceğiniz herhangi bir kullanışlı tanılama üretmez.  
  
 Bir ICE alındığında önceki sürümlerde, sorunu bildirmek için Microsoft Ürün Destek Hizmetleri'ne başvurmanız önerilir. Kullanarak **- errorreport**, Visual C# ekibine ICE bilgi sağlayabilir. Hata raporları, gelecekteki derleyici sürümleri artırmaya yardımcı olabilir.  
  
 Bir kullanıcının yeteneğini raporları göndermek için bilgisayar ve kullanıcı ilkesi izinlerine bağlıdır.  
  
 Hata ayıklayıcısı hakkında daha fazla bilgi için bkz: [Dr açıklaması. Windows (Drwtsn32.exe) aracı için Watson](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası. Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Tıklayın **derleme** özellik sayfası.  
  
3.  Tıklayın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **iç derleyici hatası raporlama** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
