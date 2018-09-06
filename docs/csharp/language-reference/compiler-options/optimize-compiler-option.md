---
title: -(C# Derleyici Seçenekleri) en iyi duruma getirme
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
ms.openlocfilehash: f8fec2c4da49aa6cac2f8dc1dc9b07c5864b837a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744005"
---
# <a name="-optimize-c-compiler-options"></a>-(C# Derleyici Seçenekleri) en iyi duruma getirme
**-En iyi duruma getirme** seçeneğini etkinleştirir veya çıkış dosyanızı daha küçük, daha hızlı ve daha verimli yapmak için derleyici tarafından gerçekleştirilen iyileştirmeleri devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **-en iyi duruma getirme** zamanında kodu en iyi duruma getirmek için ortak dil çalışma zamanı da bildirir.  
  
 Varsayılan olarak, en iyi duruma getirme devre dışıdır. Belirtin **-en iyi duruma getirme +** iyileştirmeleri etkinleştirmek için.  
  
 Bir derleme tarafından kullanılacak bir modül oluşturulurken, aynı kullanın **-en iyi duruma getirme** derleme olarak ayarlar.  
  
 **-o** öğesinin kısa biçimidir **-en iyi duruma getirme**.  
  
 Birleştirmek mümkündür **-en iyi duruma getirme** ve [-hata ayıklama](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) seçenekleri.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **derleme** özellik sayfası.  
  
3.  Değiştirme **kodu İyileştir** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `t2.cs` ve derleyici iyileştirmelerini etkinleştir:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
