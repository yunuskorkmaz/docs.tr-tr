---
title: "Yol dosya erişim hatası"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a>Yol/Dosya erişim hatası
Bir dosya erişim veya disk erişimi işlemi sırasında işletim sistemi yolunu ve dosya adı arasında bir bağlantı yapılamıyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Dosya belirtiminin doğru biçimlendirildiğinden emin olun. Bir dosya adı bir tam (mutlak) veya göreli içerebilir yolu. (Yolu, başka bir sürücüdeyse) tam nitelenmiş bir yol sürücü adıyla başlar ve kök dosyasının açık yolunu listeler. Tam olmayan tüm geçerli sürücü ve dizine göreli yoludur.  
  
2.  Varolan salt okunur dosya değiştirirler bir dosyayı kaydetmek denemedi emin olun. Bu durumda, hedef dosya salt okunur özniteliğini değiştirmek veya dosyayı farklı bir dosya adıyla kaydedin.  
  
3.  Değil dener salt okunur bir dosya olarak sıralı açmak emin olun `Output` veya `Append` modu. Bu durumda, dosyayı açma `Input` modu veya değişiklik dosyasının salt okunur özniteliği.  
  
4.  Değil dener değiştirmek emin olun bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projesi bir veritabanı veya belge içinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata türleri](../../../visual-basic/programming-guide/language-features/error-types.md)
