---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: eff367fd6cc14c655f0c623731e334054233b0a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744316"
---
# <a name="-nowarn"></a>-nowarn
Derleyicinin, uyarı oluşturma yeteneğini engeller.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`numberList`|İsteğe bağlı. Derleyici göndermeme uyarı kimliği numaralarını virgülle ayrılmış liste. Uyarı kimlikleri belirtilmezse, tüm uyarıları görüntülenmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-nowarn` Seçeneği derleyici uyarıları oluşturmaya değil neden olur. Tek bir uyarıyı bastırmak için uyarı kimliği sağlayın. `-nowarn` izleyen iki nokta üst üste seçeneği. Birden çok uyarı numaralarını virgülle ayırın.  
  
 Uyarı tanımlayıcısının yalnızca sayısal parçası belirtmeniz gerekir. Örneğin, BC42024, kullanılmayan yerel değişkenler için uyarıyı gizlemek istiyorsanız belirtin `-nowarn:42024`.  
  
 Uyarı Kimliği numaralarını hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|-Nowarn Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **derleme** sekmesi.<br />3.  Seçin **tüm uyarıları devre dışı bırak** tüm uyarıları devre dışı bırakmak için onay kutusunu işaretleyin.<br />     - veya -<br />     Belirli bir uyarı devre dışı bırakmak için **hiçbiri** uyarı bitişik aşağı açılan listeden.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` ve tüm uyarıları göstermez.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` ve kullanılmayan yerel değişkenler (42024) için uyarıları göstermez.  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Visual Basic'teki Uyarıları Yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic)
