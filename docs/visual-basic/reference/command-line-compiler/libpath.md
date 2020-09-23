---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: a91bd74d0be4f1cb223091ee2527f9567b4ca5db
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058475"
---
# <a name="-libpath"></a>-libpath

Başvurulan derlemelerin konumunu belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`dirList`|Gereklidir. Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması halinde, derleyicinin aranacağı dizinlerin noktalı virgülle ayrılmış listesi. Dizin adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  

 `-libpath`Seçeneği, [-Reference](reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.  
  
 Derleyici, aşağıdaki sırada tam olarak nitelenen derleme başvurularını arar:  
  
1. Geçerli çalışma dizini. Bu, derleyicinin çağrıldığı dizindir.  
  
2. Ortak dil çalışma zamanı sistem dizini.  
  
3. Tarafından belirtilen dizinler `-libpath` .  
  
4. LıB ortam değişkeni tarafından belirtilen dizinler.  
  
 `-libpath`Seçenek eklenebilir; bir defadan fazla belirtmek önceki değerlere ekler.  
  
 `-reference`Derleme başvurusunu belirtmek için kullanın.  
  
|Visual Studio tümleşik geliştirme ortamında Set-libpath|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Başvurular** sekmesine tıklayın.<br />3. **başvuru yolları...** düğmesine tıklayın.<br />4. **başvuru yolları** iletişim kutusunda dizin adını **klasör:** kutusuna girin.<br />5. **Klasör Ekle**'ye tıklayın.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `T2.vb` bir. exe dosyası oluşturmak için derlenir. Derleyici, C: sürücüsünün kök dizininde ve derleme başvuruları için C: sürücüsünün yeni derlemeler dizininde çalışma dizinine bakar.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
