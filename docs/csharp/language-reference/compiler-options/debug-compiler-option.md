---
title: -debug (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: ab9b299579f9ab4a854ce7ab220edc87e0c66745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218851"
---
# <a name="-debug-c-compiler-options"></a>-debug (C# Derleyici Seçenekleri)
**-Debug** seçeneği hata ayıklama bilgileri oluşturmak ve çıktı dosyası veya dosyaları yerleştirmek derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Belirtme `+`, veya yalnızca **-debug**, hata ayıklama bilgileri oluşturmak ve bir program veritabanında (.pdb dosyası) yerleştirmek derleyici neden olur. Belirtme `-`, hangi değil belirtirseniz yürürlükte olan **-debug**, hiçbir hata ayıklama bilgisi oluşturulmasına neden olur.  
  
 `full` &#124; `pdbonly`  
 Derleyici tarafından üretilen hata ayıklama bilgi türünü belirtir. Aslında, belirtmezseniz olan tam bağımsız **-debug: pdbonly**, bir hata ayıklayıcısı çalışan programa eklemeyi mümkün kılar. Kaynak kodu program hata ayıklayıcısı'ndaki başladı, ancak çalışan program hata ayıklayıcıya eklendiğinde yalnızca assembler görüntülenir, hata ayıklama pdbonly belirtebilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama yapıları oluşturmak için bu seçeneği kullanın. Varsa **-debug**, **-debug +**, veya **-debug: tam** belirtilmezse, edemeyecek programınızın çıktı dosyasında hata ayıklama.  
  
 Kullanırsanız **-debug: tam**, bazı etki hızlı ve en iyi duruma getirilmiş JIT kod boyutunu ve kod kalitesinde küçük bir etkisi açık olduğunu unutmayın **-debug: tam**. Öneririz **-debug: pdbonly** veya yayım kodunu oluşturmak için PDB.  
  
> [!NOTE]
>  Arasındaki tek fark **-debug: pdbonly** ve **-debug: tam** ile olan **-debug: tam** derleyicisi yayar bir <xref:System.Diagnostics.DebuggableAttribute>, JIT Derleyici bildirmek için kullanılır Bu hata ayıklama bilgisi yok. Bu nedenle, kodunuzu içeriyorsa bir hata iletisiyle karşılaşırsınız <xref:System.Diagnostics.DebuggableAttribute> kullanırsanız false olarak ayarlanmış **-debug: tam**.  
  
 Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz: [bir görüntü Debug kolaylaştırma](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 .Pdb dosyasının konumunu değiştirmek için bkz: [- pdb (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Tıklatın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **hata ayıklama bilgisi** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Örnek  
 Hata ayıklama bilgilerini çıktı dosyasına yerleştirin `app.pdb`:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
