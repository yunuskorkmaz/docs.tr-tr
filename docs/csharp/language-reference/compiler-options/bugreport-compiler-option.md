---
title: -bugreport (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 6e4674acd2a5edbbffd2babf130d2078019ab9b7
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331741"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (C# Derleyici Seçenekleri)
Hata ayıklama bilgileri daha sonra çözümlemek için bir dosya yerleştirilmesi gerektiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Hata raporunuzu içermesini istediğiniz dosyanın adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **- Bugreport** seçeneği belirtir, aşağıdaki bilgileri yerleştirilmelidir `file`:  
  
-   Derlemedeki tüm kaynak kodu dosyalarının bir kopyasını.  
  
-   Derlemede kullanılan derleyici seçeneklerinin bir listesi.  
  
-   Derleyici, çalıştırma ve işletim sistemi sürüm bilgisi.  
  
-   Başvurulan derlemeler ve modüller, SDK ve .NET Framework ile birlikte gelen derlemeleri hariç onaltılık basamak olarak kaydedilir.  
  
-   Derleyici çıkışı, varsa.  
  
-   İçin istenir sorun açıklaması.  
  
-   Sorun ne düşündüğünüzü açıklaması, hangi için istenir düzeltilmelidir.  
  
 Bu seçeneği ile kullandıysanız **- errorreport: istemi** veya **- errorreport: gönderme**, dosyasındaki bilgiler, Microsoft Corporation'a gönderilir.  
  
 Tüm kaynak kodu dosyalarının bir kopyasını yerleştirileceği çünkü `file`, şüpheli kod hatası kısa olası programda yeniden oluşturmak isteyebilirsiniz.  
  
 Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.  
  
 Oluşturulan dosyanın içeriğini bilgilerin yanlışlıkla açığa çıkmasına neden olabilecek kaynak kodu ortaya çıkarabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [-errorreport (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
