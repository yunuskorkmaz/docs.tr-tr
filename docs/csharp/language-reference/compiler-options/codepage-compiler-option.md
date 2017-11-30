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
ms.openlocfilehash: 37f40312f1218b8e666eae7cb2de6c768ee32108
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="codepage-c-compiler-options"></a>/codepage (C# Derleyici Seçenekleri)
Bu seçenek gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse derleme sırasında kullanılacak hangi kod sayfasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfası kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bilgisayarınızda varsayılan kod sayfası kullanmak için oluşturulmamış bir veya daha fazla kaynak kodu dosyaları derleme yaparsanız kullanabileceğiniz **/CODEPAGE** hangi kod sayfası kullanılması gerektiğini belirtmek için seçeneği. **/ CodePage** derlemeniz tüm kaynak kodu dosyaları için geçerlidir.  
  
 Kaynak kodu dosyaları bilgisayarınızda geçerli olan kod sayfası ile oluşturulan veya kaynak kodu dosyaları UNICODE veya UTF-8 ile oluşturulmuşsa kullanılmıyor ihtiyacınız varsa **/CODEPAGE**.  
  
 Bkz: [desteklendiğinin](http://go.microsoft.com/fwlink/?LinkId=148371) hangi kodu bulma hakkında bilgi için sisteminizde sayfaları desteklenir.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
