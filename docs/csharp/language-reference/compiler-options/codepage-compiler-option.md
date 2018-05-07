---
title: -codepage (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 04a0d3a62ebd2b3a938445995725994d72d5bd4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-codepage-c-compiler-options"></a>-codepage (C# Derleyici Seçenekleri)
Bu seçenek gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse derleme sırasında kullanılacak hangi kod sayfasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfası kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bilgisayarınızda varsayılan kod sayfası kullanmak için oluşturulmamış bir veya daha fazla kaynak kodu dosyaları derleme yaparsanız kullanabileceğiniz **- codepage** hangi kod sayfası kullanılması gerektiğini belirtmek için seçeneği. **-codepage** derlemeniz tüm kaynak kodu dosyaları için geçerlidir.  
  
 Kaynak kodu dosyaları bilgisayarınızda geçerli olan kod sayfası ile oluşturulan veya kaynak kodu dosyaları UNICODE veya UTF-8 ile oluşturulmuşsa kullanılmıyor ihtiyacınız varsa **- codepage**.  
  
 Bkz: [desteklendiğinin](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) hangi kodu bulma hakkında bilgi için sisteminizde sayfaları desteklenir.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
