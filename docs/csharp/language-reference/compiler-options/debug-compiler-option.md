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
ms.openlocfilehash: 4828e1cdd8b830f10b134b613bc96e69490091fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338494"
---
# <a name="-debug-c-compiler-options"></a>-debug (C# Derleyici Seçenekleri)
**-Hata ayıklama** seçeneği hata ayıklama bilgileri üret ve çıktı dosyasını veya dosyalarını yerleştirmek derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Belirtme `+`, veya yalnızca **-hata ayıklama**, derleyicinin hata ayıklama bilgileri üret ve bir program veritabanı (.pdb dosyası) yerleştirin. Belirtme `-`, hangi belirtmezseniz, geçerli olduğu **-hata ayıklama**, oluşturulacak hata ayıklama bilgisi yok neden olur.  
  
 `full` &#124; `pdbonly`  
 Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Belirtmezseniz, geçerli tam bağımsız **-debug: pdbonly**, çalışan programa hata ayıklayıcı ekleme etkinleştirir. Kaynak kodu programın hata ayıklayıcıda başlatıldı ancak çalışan programa hata ayıklayıcıya bağlı olduğu assembler yalnızca görüntüler, hata ayıklama pdbonly belirtebilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama yapıları oluşturmak için bu seçeneği kullanın. Varsa **-hata ayıklama**, **-hata ayıklama +**, veya **-debug: full** belirtilmezse, olmayacak çıkış dosyası, programınızın hata ayıklamanız mümkün.  
  
 Kullanırsanız **-debug: full**, hız ve en iyi duruma getirilmiş JIT kodunun boyutu üzerinde bazı etkiler ve kod kalitesini ile küçük bir etkisi açık olduğunu unutmayın **-debug: full**. Öneririz **-debug: pdbonly** veya kod sürüm oluşturma için hiçbir PDB.  
  
> [!NOTE]
>  Arasındaki tek fark **-debug: pdbonly** ve **-debug: full** ile olan **-debug: full** derleyici yayan bir <xref:System.Diagnostics.DebuggableAttribute>, JIT derleyicisi bildirmek için kullanılır hata ayıklama bilgilerinin kullanılabilir olduğunu. Bu nedenle, kodunuzu içeriyorsa bir hata alırsınız <xref:System.Diagnostics.DebuggableAttribute> kullanırsanız false olarak ayarlanmış **-debug: full**.  
  
 Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntü için hata ayıklama kolaylaştıracak](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 .Pdb dosyasının konumunu değiştirmek için bkz [- pdb (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin açın **özellikleri** sayfası.  
  
2. Tıklayın **derleme** özellik sayfası.  
  
3. Tıklayın **Gelişmiş** düğmesi.  
  
4. Değiştirme **hata ayıklama bilgisi** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Örnek  
 Hata ayıklama bilgilerini çıktı dosyasına yerleştirmeniz `app.pdb`:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
