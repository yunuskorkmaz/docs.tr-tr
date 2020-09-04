---
description: -Resource (C# derleyici seçenekleri)
title: -Resource (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 1e2de095b460b684fb06faf46731283a1304906e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465695"
---
# <a name="-resource-c-compiler-options"></a>-Resource (C# derleyici seçenekleri)
Belirtilen kaynağı çıkış dosyasına katıştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `filename`  
 Çıktı dosyasına eklemek istediğiniz .NET kaynak dosyası.  
  
 `identifier` (isteğe bağlı)  
 Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosya adının adıdır.  
  
 `accessibility-modifier` (isteğe bağlı)  
 Kaynağın erişilebilirliği: public veya Private. Varsayılan değer geneldir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynağı bir derlemeye bağlamak ve kaynak dosyasını çıkış dosyasına eklemek için [-linkresource](./linkresource-compiler-option.md) kullanın.  
  
 Varsayılan olarak, kaynaklar C# derleyicisi kullanılarak oluşturulduğunda derlemede ortaktır. Kaynakları özel hale getirmek için `private` erişilebilirlik değiştiricisi olarak belirtin. Veya dışında başka bir erişilebilirliği `public` olamaz `private` .  
  
 `filename`Örneğin, [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .net kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, `GetManifestResource` <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek üzere sınıfındaki yöntemleri kullanın.  
  
 **-res** , **-Resource**' in kısa biçimidir.  
  
 Çıkış dosyasındaki kaynakların sırası, komut satırında belirtilen sırada belirlenir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenize bir kaynak dosyası ekleyin.  
  
2. **Çözüm Gezgini**eklemek istediğiniz dosyayı seçin.  
  
3. **Özellikler** penceresinde dosya Için **derleme eylemi** ' ni seçin.  
  
4. **Derleme eylemini** **gömülü kaynağa**ayarlayın.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.FileProperties2.BuildAction%2A> ..  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve kaynak dosyası iliştirme `rf.resource` :  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
