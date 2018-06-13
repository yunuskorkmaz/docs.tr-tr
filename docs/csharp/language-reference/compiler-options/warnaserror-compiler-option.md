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
ms.openlocfilehash: 762db1b3d72b5b4c3d606f3517f0b384f466d231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218952"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# Derleyici Seçenekleri)
**- Warnaserror +** seçeneği tüm uyarıları hata olarak kabul eder  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Uyarıları hata olarak bunun yerine bildirilir ve yapı işlemi olarak normalde bildirilen herhangi bir iletisi (çıktı dosyaları oluşturulur) işlemi durduruldu.  
  
 Varsayılan olarak, **- warnaserror-** bir çıkış dosyasının oluşturulmasını önlemek değil uyarıları neden olur, etkilidir. **-warnaserror**, aynı olduğu **- warnaserror +**, hata olarak kabul edilmesi uyarıları oluşturulmasına neden olur.  
  
 İsteğe bağlı olarak, hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları istiyorsanız, hata olarak değerlendirmek için uyarı numaralarını virgülle ayrılmış bir listesini belirtebilir.  
  
 Kullanım [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) Derleyicinin görüntülemesini istediğiniz uyarı düzeyini belirtmek için. Kullanım [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) belirli uyarıları devre dışı bırakmak için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Değiştirme **uyarıları hata olarak kabul** özelliği.  
  
 Bu derleyici seçeneği programlı olarak ayarlamak için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve derleyici hiçbir Uyarıları görüntüle:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
