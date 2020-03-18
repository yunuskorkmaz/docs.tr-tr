---
title: -optimize (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606604"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (C# Derleyici Seçenekleri)
**-optimize etme** seçeneği, çıktı dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen optimizasyonları sağlar veya devre dışı eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **-en iyi duruma getirme,** aynı zamanda kodu çalışma zamanında en iyi duruma getirmek için ortak dil çalışma zamanını da bildirir.  
  
 Varsayılan olarak, optimizasyonlar devre dışı bırakılır. Optimizasyonları etkinleştirmek için **-optimize+** belirtin.  
  
 Bir derleme tarafından kullanılacak bir modül oluştururken, derlemenin ayarlarıyla aynı **optimize ayarları** kullanın.  
  
 **-o** **-optimize**kısa şeklidir.  
  
 **-en iyi duruma getirme** ve [hata ayıklama](./debug-compiler-option.md) seçeneklerini birleştirmek mümkündür.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. Optimize **Kodu** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>  
  
## <a name="example"></a>Örnek  
 Derleyici `t2.cs` optimizasyonlarını derle ve etkinleştirin:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
