---
title: -hedef:winexe (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606384"
---
# <a name="-targetwinexe-c-compiler-options"></a>-hedef:winexe (C# Derleyici Seçenekleri)
**-target:winexe** seçeneği derleyicinin çalıştırılabilir (EXE), Windows programı oluşturmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Çalıştırılabilir dosya .exe uzantısı ile oluşturulur. Windows programı, .NET Framework kitaplığından veya Windows API'lerinden kullanıcı arabirimi sağlayan programdır.  
  
 Konsol uygulaması oluşturmak için [-target:exe'yi](./target-exe-compiler-option.md) kullanın.  
  
 [-out](./out-compiler-option.md) seçeneğinde aksi belirtilmedikçe, çıktı dosyası adı [Ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.  
  
 Komut satırında belirtildiğinde, Windows programını oluşturmak için bir sonraki **-out** [veya-hedef](./target-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.  
  
 .exe dosyasında derlenen kaynak kod dosyalarında bir ve tek bir **Ana** yöntem gereklidir. [-ana](./main-compiler-option.md) seçenek, kodunuzu **bir Ana** yöntem ile birden fazla sınıf ait olduğu durumlarda, Hangi sınıfın **Ana** yöntemi içerdiğini belirtmenizi sağlar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Uygulama** özelliği sayfasını tıklatın.  
  
3. Çıktı **türü** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>  
  
## <a name="example"></a>Örnek  
 Bir `in.cs` Windows programına derleme:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-hedef (C# Derleyici Seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
