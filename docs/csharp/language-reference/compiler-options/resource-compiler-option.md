---
title: -Kaynak (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: ed9f4648ae632786ce860ce2c02637977f709c55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302575"
---
# <a name="-resource-c-compiler-options"></a>-Kaynak (C# Derleyici Seçenekleri)
Belirtilen kaynak çıkış dosyasına katıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyasına eklemek istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier` (isteğe bağlı)  
 Kaynağın mantıksal adı; Kaynak yüklemek için kullanılan ad. Dosya adı varsayılandır.  
  
 `accessibility-modifier` (isteğe bağlı)  
 Kaynak erişilebilirliğini: genel veya özel. Genel varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) kaynağı için bir derleme bağlama ve kaynak dosyası çıkış dosyasına ekleme.  
  
 Varsayılan olarak, C# derleyicisi kullanılarak oluşturulduğunda kaynaklar derleme içinde geneldir. Kaynakları özel hale getirmek için belirtin `private` erişilebilirlik değiştiricisi olarak. Dışındaki bir erişilebilirliğe `public` veya `private` izin verilir.  
  
 Varsa `filename` , örneğin, tarafından oluşturulmuş bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.  
  
 **-res** öğesinin kısa biçimidir **-kaynak**.  
  
 Çıkış dosyası kaynakları sırası, komut satırında belirtilen siparişi belirlenir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Bir kaynak dosyası projenize ekleyin.  
  
2. Eklemek istediğiniz dosyayı seçin **Çözüm Gezgini**.  
  
3. Seçin **derleme eylemi** dosya **özellikleri** penceresi.  
  
4. Ayarlama **derleme eylemi** için **katıştırılmış kaynak**.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve kaynak dosya ekleme `rf.resource`:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
