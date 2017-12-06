---
title: "-errorreport (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: "35"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bc8720662fb4c91953e2d399f08613f5055b1158
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2017
---
# <a name="errorreport-c-compiler-options"></a>/errorreport (C# Derleyici Seçenekleri)
Bu seçenek, bir C# derleyici iç hatası Microsoft'a bildirmek için kolay bir yol sağlar.  
  
> [!NOTE]
>  Windows Vista ve Windows Server 2008 üzerinde Visual Studio için yaptığınız hata bildirimi ayarlarını Windows hata bildirimi (WER) üzerinden yapılan ayarları geçersiz kılmaz. WER ayarları her zaman Visual Studio hata bildirimi ayarları önceliklidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Arguments  
 **yok**  
 İç derleyici hataları hakkında raporlar değil toplanmayacak veya Microsoft'a gönderilir.  
  
 **istemi**  
 Derleyici iç hatası aldığınızda, bir raporu göndermek isteyip istemediğinizi sorar. **İstemi** geliştirme ortamında bir uygulamayı derlediğinizde varsayılandır.  
  
 **sırası**  
 Hata raporu sıralar. Yönetici kimlik bilgileriyle oturum açtığınızda, günlüğe kaydedilmiş en son ne zaman bu yana hataları bildirebilirsiniz. Üç günde birden çok kez hata raporu göndermek için istenmez. **sıra** komut satırında bir uygulamayı derlediğinizde varsayılandır.  
  
 **Gönder**  
 Derleyici iç hata raporlarını otomatik olarak Microsoft'a gönderir. Bu seçeneği etkinleştirmek için önce Microsoft veri toplama ilkesini kabul etmeniz gerekir. Belirttiğiniz ilk kez **/errorreport:send** bir bilgisayarda, bir derleyici iletisi Microsoft Veri Toplama İlkesi içeren bir Web sitesine başvurur.  
    
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyasının derleyici işleyemediğinde iç derleyici hatası (çok) sonuçlanır. Bir çok oluştuğunda derleyici çıktı dosyası ya da kodunuzu düzeltmek için kullanabileceğiniz herhangi bir kullanışlı tanılama üretmez.  
  
 Bir çok alındığında önceki sürümlerde, sorunu bildirmek için Microsoft Ürün Destek Hizmetleri'ne başvurmanız önerilir. Kullanarak **/errorreport**, Visual C# ekibine çok bilgi sağlayabilir. Hata raporlarını gelecek derleyici sürümler artırmaya yardımcı olabilir.  
  
 Bir kullanıcının, raporları göndermek becerisini bilgisayar ve kullanıcı ilkesi izinlerine bağlıdır.  
  
 Hata ayıklayıcısı hakkında daha fazla bilgi için bkz: [Dr açıklaması. Windows (Drwtsn32.exe) aracı için Watson](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası. Daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Tıklatın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **iç derleyici hatası raporlama** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
