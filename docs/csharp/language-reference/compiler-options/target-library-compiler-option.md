---
title: -hedef:kütüphane (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606399"
---
# <a name="-targetlibrary-c-compiler-options"></a>-hedef:kütüphane (C# Derleyici Seçenekleri)
**-hedef:kitaplık** seçeneği derleyicinin yürütülebilir bir dosya (EXE) yerine dinamik bağlantı kitaplığı (DLL) oluşturmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Açıklamalar  
 DLL .dll uzantısı ile oluşturulur.  
  
 [-out](./out-compiler-option.md) seçeneğinde aksi belirtilmedikçe, çıktı dosyası adı ilk giriş dosyasının adını alır.  
  
 Komut satırında belirtildiğinde, .dll dosyasını oluşturmak için bir sonraki **-out** veya **-target:module** seçeneğine kadar tüm dosyalar kullanılır.  
  
 Bir .dll dosyası [yaparken, Bir Ana](../../programming-guide/main-and-command-args/index.md) yöntem gerekli değildir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Uygulama** özelliği sayfasını tıklatın.  
  
3. Çıktı **türü** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>  
  
## <a name="example"></a>Örnek  
 Derlemek `in.cs`, `in.dll`oluşturma :  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-hedef (C# Derleyici Seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
