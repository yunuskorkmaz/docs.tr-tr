---
title: -hata raporu (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253887"
---
# <a name="-errorreport-c-compiler-options"></a>-hata raporu (C# Derleyici Seçenekleri)
Bu seçenek, C# dahili derleyici hatasını Microsoft'a bildirmek için kullanışlı bir yol sağlar.

> [!NOTE]
> Windows Vista ve Windows Server 2008'de Visual Studio için yaptığınız hata raporlama ayarları, Windows Hata Raporlama (WER) aracılığıyla yapılan ayarları geçersiz kılmaz. WER ayarları her zaman Visual Studio hata raporlama ayarlarını önceliklidir.

## <a name="syntax"></a>Sözdizimi

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a>Bağımsız Değişkenler
 **yok**  
 Dahili derleyici hatalarıyla ilgili raporlar toplanmaz veya Microsoft'a gönderilmez.

 **istemi** Dahili derleyici hatası aldığınızda rapor göndermenizi ister. geliştirme ortamında bir uygulama derlediğinizde **varsayılan dır.**

 **sıra** Hata raporunu sıralar. Yönetim kimlik bilgileriyle oturum açtığınızda, son oturum açıldığınızı beri tüm hataları bildirebilirsiniz. Hatalar için üç günde bir birden fazla rapor göndermeniz istenmez. **komut** satırında bir uygulama derlediğinizde sıra varsayılandır.

 **gönder** Dahili derleyici hatalarıyla ilgili raporları otomatik olarak Microsoft'a gönderir. Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz. -hata **raporu:bilgisayarda gönder:'yi** ilk kez belirttiğinde, derleyici iletisi sizi Microsoft veri toplama ilkesini içeren bir Web sitesine yönlendirir.

## <a name="remarks"></a>Açıklamalar
 Derleyici bir kaynak kodu dosyasını işleyemediğinde dahili derleyici hatası (ICE) sonuçları. Bir ICE oluştuğunda, derleyici bir çıktı dosyası veya kodunuzu düzeltmek için kullanabileceğiniz yararlı bir tanılama üretmez.

 Önceki sürümlerde, bir ICE aldığınızda, sorunu bildirmek için Microsoft Ürün Destek Hizmetleri'ne başvurmanız tavsiye edildi. **-errorreport**kullanarak Visual C# ekibine ICE bilgileri sağlayabilirsiniz. Hata raporlarınız gelecekteki derleyici sürümlerini geliştirmeye yardımcı olabilir.

 Kullanıcının rapor gönderme yeteneği bilgisayara ve kullanıcı ilkesi izinlerine bağlıdır.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikleri** sayfasını açın. Daha fazla bilgi için Bkz. [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).

2. Özellik **Oluştur** sayfasını tıklatın.

3. **Gelişmiş** düğmesini tıklatın.

4. İç **Derleyici Hata Raporlama** özelliğini değiştirin.

 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
