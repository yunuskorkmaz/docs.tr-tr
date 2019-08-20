---
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
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602531"
---
# <a name="-resource-c-compiler-options"></a>-Resource (C# derleyici seçenekleri)
Belirtilen kaynağı çıkış dosyasına katıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyasına eklemek istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier`seçim  
 Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosya adının adıdır.  
  
 `accessibility-modifier`seçim  
 Kaynağın erişilebilirliği: public veya Private. Varsayılan değer geneldir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynağı bir derlemeye bağlamak ve kaynak dosyasını çıkış dosyasına eklemek için [-linkresource](./linkresource-compiler-option.md) kullanın.  
  
 Varsayılan olarak, kaynaklar C# derleyici kullanılarak oluşturulduğunda derlemede ortaktır. Kaynakları özel hale getirmek için erişilebilirlik değiştiricisi `private` olarak belirtin. `public` Veya`private` dışında başka bir erişilebilirliği olamaz.  
  
 , Örneğin [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. `filename` Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, çalışma zamanında `GetManifestResource` kaynağa erişmek üzere <xref:System.Reflection.Assembly> sınıfındaki yöntemleri kullanın.  
  
 **-res** , **-Resource**' in kısa biçimidir.  
  
 Çıkış dosyasındaki kaynakların sırası, komut satırında belirtilen sırada belirlenir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenize bir kaynak dosyası ekleyin.  
  
2. **Çözüm Gezgini**eklemek istediğiniz dosyayı seçin.  
  
3. **Özellikler** penceresinde dosya Için **derleme eylemi** ' ni seçin.  
  
4. **Derleme eylemini** **gömülü kaynağa**ayarlayın.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve kaynak dosyası `rf.resource`iliştirme:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
