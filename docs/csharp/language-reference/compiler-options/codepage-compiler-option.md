---
title: "-codepage (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c1181ef98ac5f335c9737771eda2b3bd9227cc9f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
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
