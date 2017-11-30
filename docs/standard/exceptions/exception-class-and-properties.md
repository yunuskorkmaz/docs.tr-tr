---
title: "Özel Durumu Sınıfı ve Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a>Özel durum sınıfı ve özellikleri

<xref:System.Exception> Sınıftır içinden özel durum devral temel sınıf. Örneğin, <xref:System.InvalidCastException> sınıf hiyerarşisi aşağıdaki gibidir:

```
Object
  Exception
    SystemException
       InvalidCastException
```

<xref:System.Exception> Sınıfı daha kolay bir özel durum anlama sağlamak aşağıdaki özellikleri vardır.

| Özellik adı | Açıklama |
| ------------- | ----------- |
| <xref:System.Exception.Data> | Bir <xref:System.Collections.IDictionary> , anahtar-değer çiftlerini rastgele verileri tutar. |
| <xref:System.Exception.HelpLink> | Bir URL (veya URN) bir özel durumun nedeni hakkında kapsamlı bilgi sağlayan bir Yardım dosyası basılı tutabilirsiniz. |
| <xref:System.Exception.InnerException> | Bu özellik, oluşturma ve özel durum işleme sırasında özel durumlar bir dizi korumak için kullanılabilir. Daha önce Yakalanan özel durumlar içeren yeni bir özel durum oluşturmak için kullanabilirsiniz. İkinci özel durum tarafından orijinal özel durumu yakalandı <xref:System.Exception.InnerException> özelliği, ek bilgileri incelemek için ikinci özel durumu işleyen kodu izin verme. Örneğin, hatalı biçimlendirilmiş bir bağımsız değişken alan bir yöntem olduğunu varsayalım.  Kod bağımsız değişkeni okumaya çalışır, ancak bir özel durum. Yöntemi özel durum yakalar ve oluşturur bir <xref:System.FormatException>. Bir özel durum nedenini belirlemek için çağıranın yeteneğini geliştirmek için onu bazen Yardımcısı yordamı tarafından oluşturulan bir özel catch ve sonra gerçekleşen hata daha hatırlanması bir özel durum için bir yöntem için önerilir. İç özel duruma başvuru için orijinal özel durumu burada ayarlanabilir yeni ve daha anlamlı bir özel durum oluşturulabilir. Bu daha anlamlı özel sonra çağırana durum. Bu işlev ile ilk oluşturulan özel durum ile biten bir dizi bağlantılı özel durumlar oluşturabilirsiniz unutmayın. |
| <xref:System.Exception.Message> | Bir özel durumun nedeni olan hakkında ayrıntılar sağlar.
| <xref:System.Exception.Source> | Alır veya uygulama veya hataya neden nesnesinin adını ayarlar. |
| <xref:System.Exception.StackTrace>| Bir hatanın oluştuğu belirlemek için kullanılan bir yığın izlemeyi içerir. Hata ayıklama bilgileri kullanılabiliyorsa, yığın izleme kaynak dosya adı ve program satır sayısını içerir. |

Devralınan sınıfların çoğu <xref:System.Exception> etmeyin ek üyeleri uygulayan veya ek işlevsellik sağlar; bunlar yalnızca devralınan <xref:System.Exception>. Bu nedenle, özel durum sınıfları, özel durum adı ve özel durum yer alan bilgileri hiyerarşideki bir özel durum için en önemli bilgiler bulunabilir.

Throw ve catch öğesinden türetilen nesneler öneririz <xref:System.Exception>, ancak türetilen herhangi bir nesne throw <xref:System.Object> sınıfı bir özel durum. Tüm diller oluşturma ve yakalama öğesinden türetilen olmayan nesneler desteklediğini unutmayın <xref:System.Exception>.
  
## <a name="see-also"></a>Ayrıca Bkz.  
[Özel durumlar](index.md)
