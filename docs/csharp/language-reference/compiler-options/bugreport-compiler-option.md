---
title: -hata raporu (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603074"
---
# <a name="-bugreport-c-compiler-options"></a>-hata raporu (C# Derleyici Seçenekleri)
Hata ayıklama bilgilerinin daha sonraki çözümleme için bir dosyaya konulması gerektiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `file`  
 Hata raporunuzu içermek istediğiniz dosyanın adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-hata raporu** seçeneği, aşağıdaki bilgilerin yerleştirilmesini `file`belirtir:  
  
- Derlemedeki tüm kaynak kod dosyalarının bir kopyası.  
  
- Derlemede kullanılan derleyici seçeneklerinin listesi.  
  
- Derleyiciniz, çalışma süreniz ve işletim sisteminiz hakkındaki sürüm bilgileri.  
  
- .NET Framework ve SDK ile birlikte sevk edilen derlemeler hariç, hexadecimal basamak olarak kaydedilen başvurulan derlemeler ve modüller.  
  
- Varsa derleyici çıktısı.  
  
- Sizden istenecek sorunun açıklaması.  
  
- Sorunun nasıl çözülmesi gerektiğini düşündüğünüze ve sizden isteneceğinin açıklaması.  
  
 Bu seçenek **-errorreport:prompt** veya **-errorreport:send**ile kullanılırsa, dosyadaki bilgiler Microsoft Corporation'a gönderilir.  
  
 Tüm kaynak kodu dosyalarının bir kopyası `file`yerleştirilecektir çünkü, şüpheli kod kusurunu mümkün olan en kısa programda çoğaltmak isteyebilirsiniz.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.  
  
 Oluşturulan dosyanın içeriğinin, yanlışlıkla bilgi ifşası ile sonuçlabilen kaynak kodu ortaya çıkardığına dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [-hata raporu (C# Derleyici Seçenekleri)](./errorreport-compiler-option.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
