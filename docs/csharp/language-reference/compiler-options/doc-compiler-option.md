---
title: "-doc (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae3d6e1ffdaaa3245a51005070b16041c16dadae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="doc-c-compiler-options"></a>/doc (C# Derleyici Seçenekleri)
**/Doc** seçeneği belge açıklamaları bir XML dosyasına yerleştirin olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Kaynak kodu dosyaları derleme açıklamalarda doldurulur XML için çıktı dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyalarında aşağıdaki koyun belge açıklamaları işlenir ve XML dosyasına eklendi:  
  
-   Gibi kullanıcı tanımlı türler bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [temsilci](../../../csharp/language-reference/keywords/delegate.md), veya [arabirimi](../../../csharp/language-reference/keywords/interface.md)  
  
-   Bu tür üyeler, bir alan olarak [olay](../../../csharp/language-reference/keywords/event.md), [özelliği](../../../csharp/programming-guide/classes-and-structs/using-properties.md), ya da yöntemi  
  
 Main içeren kaynak kodu dosyasının çıktı ilk XML'dir.  
  
 Oluşturulan .xml dosyası ile kullanılmak üzere [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, .xml dosyasının dosya adı olmasına aynı derlemeyle aynı dizinde istediğiniz .xml dosyasını emin olun ve desteklemek için derleme olduğu gibi izin verin. Bu nedenle, Visual Studio projesini derleme başvurulduğunda .xml dosyasını da bulunur. Bkz: [sağladığını kod açıklamaları](/visualstudio/ide/supplying-xml-code-comments) ve daha fazla bilgi için.  
  
 İle derleme sürece [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` içerecek \<derleme >\</assembly > çıktı dosyası için derleme bildirimi içeren dosyanın adını belirten etiketler derleme.  
  
> [!NOTE]
>  / Doc seçeneği tüm giriş dosyaları için geçerlidir; veya, proje ayarlarında projedeki tüm dosyalar ayarlayın. Belge açıklamaları için belirli bir dosya veya kodun bölümü ilgili uyarıları devre dışı bırakmak için [#pragma Uyarısı](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Bkz: [belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) yolları belgeleri açıklamaları kodunuzda oluşturmak için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** sekmesi.  
  
3.  Değiştirme **XML belge dosyası** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
