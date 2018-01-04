---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4f8a87ea3f3e551dfc84212e92f1409ef61bcba2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="libpath"></a>/libpath
Başvurulan derlemelerin konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`dirList`|Gerekli. Başvurulan bir derleme IF Bakılacak derleme için dizinler noktalı virgülle ayrılmış listesi bulunamadı ya da geçerli çalışma dizini (içinden, derleyiciyi çağırdığınız dizin) veya ortak dil çalışma zamanı 's sistem dizini. Dizin adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").|  
  
## <a name="remarks"></a>Açıklamalar  
 `/libpath` Seçeneği tarafından başvurulan derlemelerin konumunu belirtir [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneği.  
  
 Aşağıdaki sırayla tam olarak nitelenmiş değil derleme başvurularını derleyici arar:  
  
1.  Geçerli çalışma dizini. Bu, derleyicinin çağırıldığı dizindir.  
  
2.  Ortak dil çalışma zamanı sistem dizini.  
  
3.  Tarafından belirtilen dizin `/libpath`.  
  
4.  LIB ortam değişkeni tarafından belirtilen dizin.  
  
 `/libpath` Seçenektir eklenebilir; belirten daha çok kez herhangi bir önceki değeri ekler.  
  
 Kullanım `/reference` bir derleme başvurusu belirtmek için.  
  
|Tümleşik geliştirme ortamı/Libpath Visual Studio'da ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **başvuruları** sekmesi.<br />3.  Tıklatın **başvuru yolları...**  düğmesi.<br />4.  İçinde **başvuru yollarını** iletişim kutusunda, dizin adı girin **klasörü:** kutusu.<br />5.  Tıklatın **klasörü Ekle**.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` bir .exe dosyası oluşturmak için. Derleyici derleme başvuruları için çalışma dizini, C: sürücüsünün kök dizinindeki ve C: sürücüsüne yeni derlemeleri dizinini arar.  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
