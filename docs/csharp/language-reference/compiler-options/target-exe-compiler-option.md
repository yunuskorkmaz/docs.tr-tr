---
title: -hedef:exe (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606459"
---
# <a name="-targetexe-c-compiler-options"></a>-hedef:exe (C# Derleyici Seçenekleri)
**-target:exe** seçeneği derleyicinin çalıştırılabilir (EXE), konsol uygulaması oluşturmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **-target:exe** seçeneği varsayılan olarak geçerlidir. Çalıştırılabilir dosya .exe uzantısı ile oluşturulur.  
  
 Çalıştırılabilir bir Windows programı oluşturmak için [-target:winexe'yi](./target-winexe-compiler-option.md) kullanın.  
  
 [-out](./out-compiler-option.md) seçeneğinde aksi belirtilmedikçe, çıktı dosyası adı [Ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.  
  
 Komut satırında belirtildiğinde, .exe dosyasını oluşturmak için bir sonraki **-out** veya **-target:module** seçeneğine kadar tüm dosyalar kullanılır  
  
 .exe dosyasında derlenen kaynak kod dosyalarında bir ve tek bir **Ana** yöntem gereklidir. [-ana](./main-compiler-option.md) derleyici seçeneği, kodunuzun **Ana** yöntemle birden fazla sınıfa sahip olduğu durumlarda, hangi sınıfın **Ana** yöntemi içerdiğini belirtmenizi sağlar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Uygulama** özelliği sayfasını tıklatın.  
  
3. Çıktı **türü** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırlarının her `in.cs`biri `in.exe`derlenecek , oluşturma:  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-hedef (C# Derleyici Seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
