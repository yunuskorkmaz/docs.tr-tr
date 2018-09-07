---
title: Özel Durumu Sınıfı ve Özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 283b3b1aa0d56b50b6f9e67b66de3e0b68ae2331
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075526"
---
# <a name="exception-class-and-properties"></a>Özel durum sınıfı ve özellikleri

<xref:System.Exception> Özel durumları devraldığı taban sınıfı. Örneğin, <xref:System.InvalidCastException> sınıf hiyerarşisi aşağıdaki gibidir:

```
Object
  Exception
    SystemException
       InvalidCastException
```

<xref:System.Exception> Sınıfı daha kolay bir özel durum anlama sağlamak, aşağıdaki özelliklere sahiptir.

| Özellik adı | Açıklama |
| ------------- | ----------- |
| <xref:System.Exception.Data> | Bir <xref:System.Collections.IDictionary> , anahtar-değer çiftlerinde rastgele verileri tutar. |
| <xref:System.Exception.HelpLink> | Özel durumun nedeni hakkında kapsamlı bilgi sağlayan bir Yardım dosyası, URL (veya URN) barındırabilir. |
| <xref:System.Exception.InnerException> | Bu özellik, oluşturmak ve özel durum işleme sırasında özel durum bir dizi korumak için kullanılabilir. Daha önce Yakalanan özel durumların içeren yeni bir özel durum oluşturmak için kullanabilirsiniz. Özgün özel durum ikinci özel durum tarafından yakalanabilir <xref:System.Exception.InnerException> özelliği, ek bilgileri incelemek için ikinci özel durumu işleyen kodu sağlar. Örneğin, hatalı biçimlendirilmiş bir bağımsız değişken alan bir yöntem olduğunu varsayalım.  Kodu bir bağımsız değişken okumaya çalışır, ancak bir özel durum oluşturulur. Yöntemi özel durumu yakalar ve oluşturur bir <xref:System.FormatException>. Bir özel durum nedenini belirlemek için çağıranın yeteneğini artırmak için bazen bir yardımcı yordam tarafından oluşturulan bir özel durum yakalamak ve sonra gerçekleşen hata göstergesi daha özel durum için bir yöntem için uygun olabilir. Yeni ve daha anlamlı bir özel durum oluşturulabilir, özgün özel durum iç özel duruma başvuru yeri ayarlanabilir. Bu daha anlamlı ardından çağırana özel durum. Bu işlevsellik ile önce oluşturulan bir özel durum ile biten bir dizi bağlantılı özel durumları oluşturabileceğini unutmayın. |
| <xref:System.Exception.Message> | Özel durumun nedeni hakkında ayrıntılar sağlar.
| <xref:System.Exception.Source> | Alır veya uygulama ya da hataya neden nesne adını ayarlar. |
| <xref:System.Exception.StackTrace>| Bir hata oluştuğu belirlemek için kullanılan bir yığın izlemeyi içerir. Hata ayıklama bilgileri kullanılabiliyorsa, yığın izlemesi kaynak dosya adı ve program satır numarasını içerir. |

Devralınan sınıflar çoğu <xref:System.Exception> değil ek üyelerini uygulama veya ek işlevsellik sağlar; bunlar yalnızca devralınacak <xref:System.Exception>. Bu nedenle, özel durum sınıfları, özel durum adı ve özel durum'içinde yer alan bilgileri hiyerarşideki bir özel durum için en önemli bilgiler bulunabilir.

Throw ve catch öğesinden türetilen nesneler öneririz <xref:System.Exception>, ancak türetilen herhangi bir nesne oluşturabilecek <xref:System.Object> sınıfı bir özel durum olarak. Tüm diller oluşturmak ve yakalamak öğesinden türetilen olmayan nesneler sürümlerin desteklendiğini unutmayın ve <xref:System.Exception>.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
