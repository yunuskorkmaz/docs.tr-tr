---
title: -warnaserror (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503482"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# Derleyici Seçenekleri)
**-warnaserror+** seçeneği tüm uyarıları hata olarak ele almaz  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Normalde uyarı olarak bildirilecek iletiler hata olarak bildirilir ve yapı işlemi durdurulur (çıktı dosyası oluşturulmaz).  
  
 Varsayılan olarak, **-warnaserror-** geçerlidir, bu da bir çıktı dosyasının oluşumunu engellememeye neden olur. **-warnaserror**, **-warnaserror+** ile aynıdır, uyarılar hata olarak ele alınmasına neden olur.  
  
 İsteğe bağlı olarak, yalnızca birkaç özel uyarının hata olarak ele alınmasını istiyorsanız, hata olarak ele almak için virgülle ayrılmış bir uyarı numaraları listesi belirtebilirsiniz. Tüm nullability uyarılar kümesi **nullable** steno ile belirtilebilir.
  
 Derleyicinin görüntülemesini istediğiniz uyarıların düzeyini belirtmek için [-uyar'ı](./warn-compiler-option.md) kullanın. Bazı [-nowarn](./nowarn-compiler-option.md) uyarıları devre dışı kullanabilirsiniz.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. Uyarıları **Hata Olarak Ele'de** değiştirin özelliği.  
  
 Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>ayarlamak için bkz.  
  
## <a name="example"></a>Örnek  
 Derleyicinin hiçbir uyarı görüntülemesini `in.cs` ve derlemesini ve görüntülemesini gerek:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
