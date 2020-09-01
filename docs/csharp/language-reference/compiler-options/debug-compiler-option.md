---
description: -Debug (C# derleyici seçenekleri)
title: -Debug (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 164530a5ec99e7d5b9f34dbcdfb18d80f3102308
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125923"
---
# <a name="-debug-c-compiler-options"></a>-Debug (C# derleyici seçenekleri)
**-Debug** seçeneği derleyicinin hata ayıklama bilgileri oluşturmasına ve bunu çıkış dosyasına veya dosyalarına yerleştirmesine neden olur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `+` &#124; `-`  
 `+`Veya yalnızca **hata ayıklama**belirtildiğinde, derleyicinin hata ayıklama bilgileri oluşturmasına ve bir program veritabanına (. pdb dosyası) yerleştirmesine neden olur. `-` **Hata ayıklama**belirtmezseniz, etkin olan ve hata ayıklama bilgilerinin oluşturulmasına neden olan öğesini belirtme.  
  
 `full` &#124; `pdbonly`  
 Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. **-Debug: pdbonly**belirtmezseniz geçerli olan tam bağımsız değişken, çalışan programa hata ayıklayıcı iliştirmeyi sağlar. Yalnızca program hata ayıklayıcıda başlatıldığında, pdbyalnızca kaynak kodu hata ayıklamasına izin verir, ancak çalışan program hata ayıklayıcıya eklendiğinde yalnızca assembler görüntülenir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama derlemeleri oluşturmak için bu seçeneği kullanın. **-** Debug, **-Debug +** veya **-Debug: Full** belirtilmemişse, programınızın çıkış dosyasında hata ayıklayamazsınız.  
  
 **-Debug: Full**KULLANıRSANıZ, JIT ile iyileştirilmiş kodun hız ve boyutunu ve **-Debug: Full**ile kod kalitesiyle ilgili küçük bir etkisi olduğunu unutmayın. **Hata ayıklamanızı öneririz: yalnızca pdbonly** veya sürüm kodu oluşturmak için pdb yok.  
  
> [!NOTE]
> **-Debug: pdbonly** ve **-Debug: Full** arasında bir farklılık vardır **-hata** ayıklama: Full derleyici, <xref:System.Diagnostics.DebuggableAttribute> JIT derleyicisine hata ayıklama bilgilerinin kullanılabilir olduğunu bildirmek için kullanılan bir yayar. Bu nedenle, <xref:System.Diagnostics.DebuggableAttribute> **-Debug: Full**kullanırsanız kodunuz false olarak ayarla ' yı içeriyorsa bir hata alırsınız.  
  
 Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntüyü hata ayıklamayı kolaylaştırın](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 . Pdb dosyasının konumunu değiştirmek için, bkz: [-pdb (C# derleyici seçenekleri)](./pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Gelişmiş** düğmesine tıklayın.  
  
4. **Hata ayıklama bilgisi** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A> ..  
  
## <a name="example"></a>Örnek  
 Hata ayıklama bilgilerini çıkış dosyasına yerleştir `app.pdb` :  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
