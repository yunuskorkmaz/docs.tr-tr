---
title: -warn (C# Derleyici Seçenekleri)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602398"
---
# <a name="-warn-c-compiler-options"></a>-warn (C# Derleyici Seçenekleri)
**-uyarseçeneği** derleyicinin görüntülenmesi için uyarı düzeyini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `option`  
 Derleme için görüntülenmesini istediğiniz uyarı düzeyi: Daha düşük sayılar yalnızca yüksek önem uyarılarını gösterir; daha yüksek sayılar daha fazla uyarı gösterir. Geçerli değerler 0-4:  
  
|Uyarı düzeyi|Anlamı|  
|-------------------|-------------|  
|0|Tüm uyarı iletilerinin emisyonunu kapatır.|  
|1|Ciddi uyarı iletileri görüntüler.|  
|2|Düzey 1 uyarılarının yanı sıra sınıf üyelerini gizleme yle ilgili uyarılar gibi belirli, daha az ciddi uyarıları görüntüler.|  
|3|Düzey 2 uyarılarının yanı sıra, her zaman değer biçilen `true` ifadeler `false`hakkındaki uyarılar gibi belirli, daha az ciddi uyarıları görüntüler.|  
|4 (varsayılan)|Tüm düzey 3 uyarıları ve bilgilendirme uyarılarını görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata veya uyarı hakkında bilgi almak için Yardım Dizini'ndeki hata kodunu alabilirsiniz. Bir hata veya uyarı hakkında bilgi almanın diğer yolları için [C# Derleyici Hataları'na](../compiler-messages/index.md)bakın.  
  
 Tüm uyarıları hata olarak ele almak için [-warnaserror'ı](./warnaserror-compiler-option.md) kullanın. Bazı [-nowarn](./nowarn-compiler-option.md) uyarıları devre dışı kullanabilirsiniz.  
  
 **-w** kısa şeklidir **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. Uyarı **Düzeyi** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>  
  
## <a name="example"></a>Örnek  
 Derleyiciyi yalnızca seviye 1 uyarıları tazyin `in.cs` ve derleyiciye sahip  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
