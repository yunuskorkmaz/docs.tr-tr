---
description: -warn (C# derleyici seçenekleri)
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
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 55e80d0bd05e2119154210503bb277d743050e18
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139079"
---
# <a name="-warn-c-compiler-options"></a>-warn (C# derleyici seçenekleri)
**-Warn** seçeneği derleyicinin görüntüleyeceği uyarı düzeyini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `option`  
 Derleme için görüntülenmesini istediğiniz uyarı düzeyi: daha düşük sayılar yalnızca yüksek önem derecesine sahip uyarıları gösterir; daha yüksek numaralar daha fazla uyarı gösterir. Değer sıfır veya pozitif bir tamsayı olmalıdır:

|Uyarı düzeyi|Anlamı|
|-------------------|-------------|
|0|Tüm uyarı iletilerinin emisyonunu kapatır.|
|1|Ciddi uyarı iletileri görüntüler.|  
|2|Düzey 1 uyarılarını ve sınıf üyelerini gizleme hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler.|  
|3|Düzey 2 uyarılarını ve her zaman veya olarak değerlendirme yapan ifadeler hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler `true` `false` .|  
|4 (varsayılan)|Tüm düzey 3 uyarılarını ve bilgilendirici uyarıları görüntüler.|
|5|4. düzey uyarıları ve C# 9,0 ile gönderilen derleyicinin [ek uyarılarını](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) görüntüler.|
|5 ' ten büyük|5 ' ten büyük bir değer 5 olarak kabul edilir. Genellikle rastgele büyük bir değer (örneğin,), `9999` derleyici yeni uyarı düzeyleriyle güncelleştirilirse her zaman tüm uyarılara sahip olduğunuzdan emin olmanızı sağlar.|
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata veya uyarı hakkında bilgi almak için yardım dizinindeki hata kodunu arayabilirsiniz. Bir hata veya uyarı hakkında bilgi almanın diğer yolları için bkz. [C# derleyici hataları](../compiler-messages/index.md).  
  
 Tüm uyarıları hata olarak değerlendirmek için [-warnaserror](./warnaserror-compiler-option.md) kullanın. Belirli uyarıları devre dışı bırakmak için [-nowarn](./nowarn-compiler-option.md) kullanın.  
  
 **-w** , **-Warn**kısa biçimidir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Uyarı düzeyi** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A> ..  
  
## <a name="example"></a>Örnek  
 Derleyin `in.cs` ve derleyicinin yalnızca düzey 1 uyarılarını görüntülemesini sağlayabilirsiniz:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
