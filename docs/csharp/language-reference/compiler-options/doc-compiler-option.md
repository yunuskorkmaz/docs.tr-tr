---
title: -doc (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
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
ms.openlocfilehash: 7c8fc11c8799912ea6340940ccd254ae82519591
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591687"
---
# <a name="-doc-c-compiler-options"></a>-doc (C# Derleyici Seçenekleri)
**-Doc** seçenek belge yorumlarını bir XML dosyasında yerleştirmenize olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Çıkış dosyası için derleme kaynak kod dosyalarını yorumlarda doldurulur XML.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyalarında aşağıdaki önünde belge açıklamaları işlenir ve XML dosyasına eklendi:  
  
- Gibi kullanıcı tanımlı türler bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [temsilci](../../../csharp/language-reference/keywords/delegate.md), veya [arabirimi](../../../csharp/language-reference/keywords/interface.md)  
  
- Bir alan olarak tür üyeleri [olay](../../../csharp/language-reference/keywords/event.md), [özelliği](../../../csharp/programming-guide/classes-and-structs/using-properties.md), veya yöntemi  
  
 Ana içeren kaynak kodu dosyasının çıkış önce XML öğesine var.  
  
 Oluşturulan .xml dosyası ile kullanılmak üzere [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, aynı olması, istediğiniz .xml dosyasını emin olun ve desteklemek için derleme derleme olarak aynı dizinde olduğundan .xml dosyasının dosya adı sağlar. Bu nedenle, Visual Studio projesinde derlemeye başvurulduğundan, .xml dosyasını da bulunur. Bkz: [kodu açıklamalarını sağlama](/visualstudio/ide/supplying-xml-code-comments) ve daha fazla bilgi için.  
  
 Derleme sürece [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` içerecek \<derleme > \< /Assembly > etiketleri çıktı dosyası için derleme bildirimini içeren dosya adını belirtme derleme.  
  
> [!NOTE]
>  Doc seçenek, tüm giriş dosyaları için geçerlidir veya proje ayarlarında, projedeki tüm dosyalar. Belge açıklamaları için belirli dosya veya kod bölümüne ilgili uyarıları devre dışı bırakmak için [#pragma Uyarısı](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Bkz: [belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) kodunuza yorumlar gelen belgeleri oluşturmak yöntemleri.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin açın **özellikleri** sayfası.  
  
2. Tıklayın **derleme** sekmesi.  
  
3. Değiştirme **XML belge dosyası** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
