---
title: -hata ayıklama (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 8bb2b411dc867b6a43e52058dccf2ac980cf0b1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922507"
---
# <a name="-debug-c-compiler-options"></a>-hata ayıklama (C# Derleyici Seçenekleri)
**Hata ayıklama** seçeneği derleyicinin hata ayıklama bilgilerini oluşturmasına ve çıktı dosyasına veya dosyalarına yerleştirmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `+`&#124;`-`  
 Belirtilmesi, `+`veya yalnızca **hata ayıklama,** derleyicinin hata ayıklama bilgileri oluşturmasına ve bunu bir program veritabanına (.pdb dosyası) yerleştirmesine neden olur. `-` **-hata ayıklama**belirtmezseniz geçerli olan , geçerli olan belirtilmesi, hata ayıklama bilgisi nin oluşturulmamasını neden olur.  
  
 `full`&#124;`pdbonly`  
 Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. **-debug:pdbonly**belirtmezseniz geçerli olan tam bağımsız değişken, çalışan programa bir hata ayıklama eklemeyi sağlar. Pdbonly belirtilmesi, program hata ayıklayıcıda başlatıldığında kaynak kodunun hata ayıklanmasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde assembler görüntülenir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama yapılarını oluşturmak için bu seçeneği kullanın. **-hata ayıklama,** **-hata ayıklama+** veya **-hata ayıklama:tam** belirtilmemişse, programınızın çıktı dosyasını hata ayıklama nız mümkün olmayacaktır.  
  
 **-debug:full**kullanıyorsanız, JIT optimize edilmiş kodun hızı ve boyutu üzerinde bazı etkiler ve **-hata ayıklama:tam**ile kod kalitesi üzerinde küçük bir etkisi olduğunu unutmayın. Sürüm kodu oluşturmak için **-debug:pdbonly** veya pdb'yi öneririz.  
  
> [!NOTE]
> **-debug:pdbonly** ve **-debug:full** arasındaki farklardan biri, **-debug:full** derleyicinin hata ayıklama bilgilerinin kullanılabilir olduğunu JIT derleyicisine söylemek için kullanılan bir <xref:System.Diagnostics.DebuggableAttribute>, yayar. Bu nedenle, <xref:System.Diagnostics.DebuggableAttribute> **-debug:full**kullanırsanız kodunuz yanlış kümesi içeriyorsa bir hata alırsınız.  
  
 Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için [bkz.](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
  
 .pdb dosyasının konumunu değiştirmek için bkz. [-pdb (C# Derleyici Seçenekleri)](./pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. **Gelişmiş** düğmesini tıklatın.  
  
4. Hata **Ayıklama Bilgileri** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>  
  
## <a name="example"></a>Örnek  
 Çıktı dosyasına `app.pdb`hata ayıklama bilgilerini yerleştirin:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
