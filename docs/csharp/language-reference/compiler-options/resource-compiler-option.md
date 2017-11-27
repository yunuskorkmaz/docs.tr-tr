---
title: "-resource (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 726956275436e22723bc32b98b2b8b7c7df5fb12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="resource-c-compiler-options"></a>/resource (C# Derleyici Seçenekleri)
Belirtilen kaynak çıkış dosyası içine katıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıktı dosyasına eklemek istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier`(isteğe bağlı)  
 Kaynak için mantıksal ad; Kaynak yüklemek için kullanılan ad. Varsayılan dosya adıdır.  
  
 `accessibility-modifier`(isteğe bağlı)  
 Kaynak erişilebilirliğini: genel veya özel. Ortak varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) bir derlemeye bir kaynak bağlayın ve kaynak dosyası çıktı dosyasına ekleme.  
  
 C# Derleyici kullanılarak oluşturulduğunda varsayılan olarak, derlemede ortak kaynaklardır. Kaynakları özel hale getirmek için belirtmeniz `private` olarak erişim değiştiricisi. Dışındaki bir erişilebilirliğe `public` veya `private` izin verilir.  
  
 Varsa `filename` , örneğin, tarafından oluşturulan bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.  
  
 **/ res** kısa biçimi olan **/Resource**.  
  
 Çıktı dosyası kaynaklarında sırasını, komut satırında belirtilen sipariş belirlenir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Kaynak dosyayı projenize ekleyin.  
  
2.  İçinde eklemek istediğiniz dosyayı seçin **Çözüm Gezgini**.  
  
3.  Seçin **yapı eylemi** dosyasını **özellikleri** penceresi.  
  
4.  Ayarlama **yapı eylemi** için **katıştırılmış kaynak**.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve kaynak dosyası ekleme `rf.resource`:  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
