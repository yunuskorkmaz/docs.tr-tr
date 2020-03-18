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
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73422967"
---
# <a name="-doc-c-compiler-options"></a>-doc (C# Derleyici Seçenekleri)
**-doc** seçeneği, belge açıklamalarını bir XML dosyasına yerleştirmenize olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `file`  
 Derlemenin kaynak kodu dosyalarındaki açıklamalarla doldurulan XML'nin çıktı dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kod dosyalarında, aşağıdakilerden önce gelen dokümantasyon açıklamaları işlenebilir ve XML dosyasına eklenebilir:  
  
- [Sınıf,](../keywords/class.md) [temsilci](../builtin-types/reference-types.md#the-delegate-type)veya [arabirim](../keywords/interface.md) gibi kullanıcı tanımlı türler  
  
- Alan, [olay,](../keywords/event.md) [özellik](../../programming-guide/classes-and-structs/using-properties.md)veya yöntem gibi üyeler  
  
 Main'i içeren kaynak kod dosyası ilk olarak XML'e çıkar.  
  
 Oluşturulan .xml dosyasını [IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle kullanmak için kullanmak için ,.xml dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasını ve ardından .xml dosyasının derlemeyle aynı dizinde olduğundan emin olmasını sağlar. Böylece, derleme Visual Studio projesinde başvurulduğunda, .xml dosyası da bulunur. Bkz. [Kod Açıklamaları Sağlama](/visualstudio/ide/reference/generate-xml-documentation-comments) ve daha fazla bilgi için.  
  
 [-target:module](./target-module-compiler-option.md)ile derlemediğiniz `file` sürece, \<derlemenin çıktı dosyası için derleme bildirimini içeren dosyanın adını belirten derleme>\</derleme> etiketleri içerecektir.  
  
> [!NOTE]
> -doc seçeneği tüm giriş dosyaları için geçerlidir; veya Proje Ayarları'nda ayarlanmışsa, projedeki tüm dosyalar. Belirli bir dosya veya kod bölümü için belge açıklamalarıyla ilgili uyarıları devre dışı kullanabilirsiniz, [#pragma uyarıkullanın.](../preprocessor-directives/preprocessor-pragma-warning.md)  
  
 Kodunuzdaki yorumlardan belge oluşturma yolları için [Belgeler Için Önerilen Etiketlere](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) bakın Açıklamalar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Yapı** sekmesini tıklatın.  
  
3. **XML dokümantasyon dosyası** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
