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
ms.openlocfilehash: 2ae555c2e049e687f508e62b5b46fd8a744e827f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329109"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# Derleyici Seçenekleri)
**- Warnaserror +** seçeneği, tüm uyarıları hata olarak davranır  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Uyarıları hata olarak bunun yerine bildirilir ve yapı işlemi olarak normalde bildirilebilecek herhangi bir iletiyi (çıkış dosyaları oluşturulur) durdu.  
  
 Varsayılan olarak, **- warnaserror-** olmayan bir çıkış dosyasının oluşturulmasını önlemek uyarılara neden aslında olduğu. **-warnaserror**, aynı olduğu **- warnaserror +**, uyarıları hata olarak kabul edilmesine neden olur.  
  
 İsteğe bağlı olarak, isterseniz hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları hata olarak değerlendirilecek uyarıların virgülle ayrılmış bir listesini belirtebilirsiniz.  
  
 Kullanım [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) derleyici görüntülemek için istediğiniz uyarı düzeyini belirtmek için. Kullanım [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) belirli uyarıları devre dışı.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin açın **özellikleri** sayfası.  
  
2. Tıklayın **derleme** özellik sayfası.  
  
3. Değiştirme **uyarıları hata olarak değerlendir** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve derleyicinin hiçbir uyarılar:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
