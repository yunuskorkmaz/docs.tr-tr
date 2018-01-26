---
title: "-warnaserror (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a341fe9760d7fdb0e4df7046cf356e550b4adb9
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2018
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
