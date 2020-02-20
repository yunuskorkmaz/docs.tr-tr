---
title: -warnaserror (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503482"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# derleyici seçenekleri)
**-Warnaserror +** seçeneği tüm uyarıları hata olarak değerlendirir  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Normalde uyarı olarak bildirilen tüm iletiler, bunun yerine hata olarak bildirilir ve derleme işlemi durdurulur (çıktı dosyası derlenmemiştir).  
  
 Varsayılan olarak, **-warnaserror-** , bir çıkış dosyasının oluşturulmasını engellemez uyarısı oluşmasına neden olur. \- **warnaserror +** ile aynı olan **warnaserror**, uyarıların hata olarak işlenmesine neden olur.  
  
 İsteğe bağlı olarak, yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz. Tüm null olabilme uyarıları kümesi **Nullable toplu değer** ile belirtilebilir.
  
 Derleyicinin görüntülemesini istediğiniz uyarı düzeyini belirtmek için [-Warn](./warn-compiler-option.md) kullanın. Belirli uyarıları devre dışı bırakmak için [-nowarn](./nowarn-compiler-option.md) kullanın.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Uyarıları hata olarak değerlendir** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Örnek  
 `in.cs` derleyin ve derleyicinin hiçbir uyarı görüntülememesine sahip olamaz:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
