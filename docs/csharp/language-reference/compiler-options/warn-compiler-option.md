---
title: -warn (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 5b05e944a37e16fc1fcc422271be00c09a271a33
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602398"
---
# <a name="-warn-c-compiler-options"></a>-warn (C# derleyici seçenekleri)
**-Warn** seçeneği derleyicinin görüntüleyeceği uyarı düzeyini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Derleme için görüntülenmesini istediğiniz uyarı düzeyi: Daha düşük sayılar yalnızca yüksek önem derecesine sahip uyarıları gösterir; daha yüksek numaralar daha fazla uyarı gösterir. Geçerli değerler 0-4 ' dir:  
  
|Uyarı düzeyi|Açıklama|  
|-------------------|-------------|  
|0|Tüm uyarı iletilerinin emisyonunu kapatır.|  
|1\.|Ciddi uyarı iletileri görüntüler.|  
|2|Düzey 1 uyarılarını ve sınıf üyelerini gizleme hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler.|  
|3|Düzey 2 uyarılarını ve her zaman veya `true` `false`olarak değerlendirme yapan ifadeler hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler.|  
|4 (varsayılan)|Tüm düzey 3 uyarılarını ve bilgilendirici uyarıları görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata veya uyarı hakkında bilgi almak için yardım dizinindeki hata kodunu arayabilirsiniz. Bir hata veya uyarı hakkında bilgi almanın diğer yolları için bkz [ C# . derleyici hataları](../compiler-messages/index.md).  
  
 Tüm uyarıları hata olarak değerlendirmek için [-warnaserror](./warnaserror-compiler-option.md) kullanın. Belirli uyarıları devre dışı bırakmak için [-nowarn](./nowarn-compiler-option.md) kullanın.  
  
 **-w** , **-Warn**kısa biçimidir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Uyarı düzeyi** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## <a name="example"></a>Örnek  
 Derleyin `in.cs` ve derleyicinin yalnızca düzey 1 uyarılarını görüntülemesini sağlayabilirsiniz:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
