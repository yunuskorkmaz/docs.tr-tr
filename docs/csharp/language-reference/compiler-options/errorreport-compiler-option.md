---
title: -errorreport (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: dc876f609643b7112c0f54574bd202c7c19cb119
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924777"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (C# derleyici seçenekleri)
Bu seçenek, Microsoft 'a C# iç derleyici hatası bildirmek için kullanışlı bir yol sağlar.  
  
> [!NOTE]
> Windows Vista ve Windows Server 2008 ' de, Visual Studio için yaptığınız hata raporlama ayarları Windows Hata Bildirimi (WER) ile yapılan ayarları geçersiz kılmaz. WER ayarları her zaman Visual Studio hata raporlama ayarlarından önceliklidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Arguments  
 **seçim**  
 İç derleyici hataları hakkında raporlar toplanmayacak veya Microsoft 'a gönderilmez.  
  
 **isteme**  
 İç derleyici hatası aldığınızda rapor göndermenizi ister. geliştirme ortamında bir uygulama derlerken varsayılan değer, **istem** varsayılandır.  
  
 **Sıradaki**  
 Hata raporunu sıralar. Yönetici kimlik bilgileriyle oturum açtığınızda, son oturum açtığınız zamandan bu yana tüm sorunları bildirebilirsiniz. Her üç günde birden çok kez rapor göndermeniz istenmez. komut satırında bir uygulama derlerken varsayılan **kuyruk** varsayılandır.  
  
 **Gönder**  
 , İç derleyici hatalarının raporlarını otomatik olarak Microsoft 'a gönderir. Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz. Bir bilgisayarda **-errorreport: Send** ' i ilk kez belirttiğinizde, bir derleyici Iletisi sizi Microsoft veri toplama ilkesini Içeren bir Web sitesine başvuracaktır.  
    
## <a name="remarks"></a>Açıklamalar  
 Derleyici bir kaynak kodu dosyasını işleyeişce bir iç derleyici hatası (ıCE) oluşur. Bir buz gerçekleştiğinde, derleyici bir çıkış dosyası ya da kodunuzu onarmak için kullanabileceğiniz yararlı bir tanılama üretmez.  
  
 Önceki sürümlerde, bir buz aldığınızda sorunu bildirmek için Microsoft Ürün Destek Hizmetleri 'ne başvurmanız önerilir. **-Errorreport**kullanarak, görsel C# ekibe buz bilgileri sağlayabilirsiniz. Hata raporlarınız, gelecekteki derleyici sürümlerinin artırılmasına yardımcı olabilir.  
  
 Kullanıcının raporları gönderebilme özelliği bilgisayar ve Kullanıcı ilkesi izinlerine bağlıdır.  
  
 Hata ayıklayıcı hakkında daha fazla bilgi için bkz [. Dr açıklaması. Windows için Watson (Drwtsn32. exe) aracı](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın. Daha fazla bilgi için bkz. [derleme sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Gelişmiş** düğmesine tıklayın.  
  
4. **Iç derleyici hata raporlama** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
