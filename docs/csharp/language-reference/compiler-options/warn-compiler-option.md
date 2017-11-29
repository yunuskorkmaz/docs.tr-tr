---
title: "-warn (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab5748f43777ec545e76100543473785894461cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="warn-c-compiler-options"></a>/warn (C# Derleyici Seçenekleri)
**/ Warn** seçeneği derleyici görüntülenecek uyarı düzeyini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/warn:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Derleme için görüntülenmesini istediğiniz uyarı düzeyini: küçük numaralar yalnızca yüksek öneme sahip uyarılar; büyük sayılar daha fazla uyarıyı gösterir. Geçerli değerler 0-4 şunlardır:  
  
|Uyarı düzeyi|Açıklama|  
|-------------------|-------------|  
|0|Tüm uyarı iletilerini yayımlanmasını devre dışı bırakır.|  
|1.|Önemli uyarı iletileri görüntülenir.|  
|2|Düzey 1 uyarıları artı bazı, görüntüler, sınıf üyelerini gizleme uyarıları gibi daha düşük öneme sahip uyarılar.|  
|3|Düzey 2 uyarıları görüntüler için her zaman değerlendirin ifadeler hakkında uyarılar gibi belirli, daha az önemli uyarıları artı `true` veya `false`.|  
|4 (varsayılan)|Tüm görüntüler 3 uyarıları ve bilgilendirici uyarılar düzeyi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata veya uyarı hakkında bilgi almak için Yardım dizini hata kodunu arayabilirsiniz. Bir hata veya uyarı hakkında bilgi almak diğer yolları için bkz: [C# derleyici hataları](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Kullanım [/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) tüm uyarıları hata olarak değerlendirmek için. Kullanım [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) belirli uyarıları devre dışı bırakmak için.  
  
 **/w** kısa biçimi olan **/ warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Değiştirme **uyarı düzeyi** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve derleyicinin yalnızca düzey 1 Uyarıları görüntüle:  
  
```console  
csc /warn:1 in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
