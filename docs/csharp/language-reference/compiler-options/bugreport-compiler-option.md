---
description: -bugreport (C# derleyici seçenekleri)
title: -bugreport (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 2afab44eec0c7bcc9809b458be0348093cb6dd07
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196825"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (C# derleyici seçenekleri)

Hata ayıklama bilgilerinin daha sonra analiz edilmek üzere bir dosyaya yerleştirilmesi gerektiğini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `file`  
 Hata raporunuzu içermesini istediğiniz dosyanın adı.  
  
## <a name="remarks"></a>Açıklamalar  

 **-Bugreport** seçeneği aşağıdaki bilgilerin yerleştirilmesi gerektiğini belirtir `file` :  
  
- Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.  
  
- Derlemede kullanılan derleyici seçeneklerinin bir listesi.  
  
- Derleyici, çalışma zamanı ve işletim sistemi ile ilgili sürüm bilgileri.  
  
- Başvurulan derlemeler ve modüller, .NET Framework ve SDK ile birlikte gelen derlemeler hariç, onaltılık basamaklar olarak kaydedilir.  
  
- Varsa derleyici çıkışı.  
  
- Probleme için sizden sorulacak bir açıklama.  
  
- Sorunun düzeltilmesi hakkında bir açıklama ve sizden istenir.  
  
 Bu seçenek **-errorreport: Prompt** veya **-errorreport: Send**ile kullanılırsa, dosyadaki bilgiler Microsoft Corporation 'a gönderilir.  
  
 Tüm kaynak kodu dosyalarının bir kopyası içine yerleştirilecek `file` , olası en kısa programda şüpheli kod hatasını yeniden oluşturmak isteyebilirsiniz.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
 Oluşturulan dosyanın içeriğinin, yanlışlıkla bilginin açığa çıkmasına neden olabilecek kaynak kodu kullanıma sunduğuna dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [-errorreport (C# derleyici seçenekleri)](./errorreport-compiler-option.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
