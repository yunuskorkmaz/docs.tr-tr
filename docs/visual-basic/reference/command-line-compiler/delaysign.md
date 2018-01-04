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
ms.openlocfilehash: b4d29f99d0c375eebee0f477720cb9a22172dddb
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
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
  
 Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi için.  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>Tümleşik geliştirme ortamı/delaysign Visual Studio'da ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**.   
  
2.  Tıklatın **imzalama** sekmesi.  
  
3.  Değer kümesinde **gecikme yalnızca oturum** kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
