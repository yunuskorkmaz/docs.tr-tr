---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c42e351808281d90eafdb6e61a3f1736ef15c9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign"></a>/delaysign
Derlemenin tamamen veya kısmen imzalanacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Kullanım `/delaysign-` tam imzalı bir derleme istiyorsanız. Kullanım `/delaysign+` imzalı karma için derleme ve ayrılmış alanı ortak anahtarı koyun istiyorsanız. Varsayılan, `/delaysign-` değeridir.  
  
## <a name="remarks"></a>Açıklamalar  
 `/delaysign` Seçeneği hiçbir etkisi ile kullanılmadığı sürece [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) veya [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Tam imzalı bir derleme istediğinde bildirimi (derleme meta verilerini) içeren ve karmayı özel anahtarıyla imzalar dosyayı derleyici karma hale getirir. Elde edilen dijital imza, bildirimi içeren dosyada depolanır. Bir derlemeyi imzalı gecikme olduğunda derleyici işlem değil ve daha sonra imzanın eklenmesi için imza ancak yedekleri alanı dosyasında depolamak.  
  
 Kullanarak örneğin, `/delaysign+`, bir kuruluştaki bir geliştirici sınayıcılar genel derleme önbelleği ile kaydetmek ve kullanabilecek bir derlemeyi imzasız test sürümlerini dağıtabilirsiniz. Derleme üzerinde iş tamamlandığında, kuruluşunuzun özel anahtarı sorumlu kişi derleme tam olarak oturum açabilir. Bu compartmentalization tüm geliştiricilerin derlemelerini sağlarken kuruluşunuzun özel anahtarı ifşaatına karşı korur.  
  
 Bkz: [bkz](https://msdn.microsoft.com/library/xwb8f617) derleme imzalama hakkında daha fazla bilgi için.  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>Tümleşik geliştirme ortamı/delaysign Visual Studio'da ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Tıklatın **imzalama** sekmesi.  
  
3.  Değer kümesinde **gecikme yalnızca oturum** kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [/ keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
