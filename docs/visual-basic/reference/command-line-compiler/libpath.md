---
title: -LIBPATH
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b8e28b821f6536ddb5c7612e8706e024dd79a0bd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833335"
---
# <a name="-libpath"></a>-LIBPATH
Başvurulan bütünleştirilmiş kodların konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`dirList`|Gerekli. Sahipse başvurulan bir derleme aramak derleyicinin dizinlerin noktalı virgülle ayrılmış listesi bulunamadı veya geçerli çalışma dizinine (içinden, derleyiciyi çağırdığınız dizin) veya ortak dil çalışma zamanının sistem dizini. Dizin adı boşluk içeriyorsa adı tırnak içine alın. ("").|  
  
## <a name="remarks"></a>Açıklamalar  
 `-libpath` Seçeneği tarafından başvurulan derlemelerin konumunu belirten [-başvuru](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneği.  
  
 Derleyici şu sıralamadaki tam olmayan bütünleştirilmiş kod başvuruları arar:  
  
1.  Geçerli çalışma dizini. Bu, derleyicinin çağırıldığı dizinidir.  
  
2.  Ortak dil çalışma zamanı sistem dizini.  
  
3.  Tarafından belirtilen dizinlerde `/libpath`.  
  
4.  LIB ortam değişkeni tarafından belirtilen dizinler.  
  
 `-libpath` Eklenebilir; belirtme seçeneği, birden çok kez önceki tüm değerlere ekler.  
  
 Kullanım `-reference` bir bütünleştirilmiş kod başvurusu belirtmek için.  
  
|/ Libpath Visual Studio'da ayarlamak için tümleşik geliştirme ortamı|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **başvuruları** sekmesi.<br />3.  Tıklayın **başvuru yolları...**  düğmesi.<br />4.  İçinde **başvuru yolları** iletişim kutusunda, dizin adı girin **klasör:** kutusu.<br />5.  Tıklayın **klasörü Ekle**.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` bir .exe dosyası oluşturmak için. Derleyici, derleme başvuruları için çalışma dizininde, C: sürücüsünün kök dizinindeki ve C: sürücüsünde yeni derlemeler dizininde arar.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
