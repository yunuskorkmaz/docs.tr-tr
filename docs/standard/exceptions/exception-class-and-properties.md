---
title: Özel Durumu Sınıfı ve Özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
ms.openlocfilehash: df05150a5bdd5d24766be252f5cec9a436720d8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708951"
---
# <a name="exception-class-and-properties"></a>Özel durum sınıfı ve özellikleri

Sınıf, <xref:System.Exception> özel durumların devraldığı taban sınıftır. Örneğin, <xref:System.InvalidCastException> sınıf hiyerarşisi aşağıdaki gibidir:

<xref:System.Object>\
&nbsp;&nbsp;<xref:System.Exception>\
&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.SystemException>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.InvalidCastException>

Sınıf, <xref:System.Exception> özel durumu anlamayı kolaylaştıran aşağıdaki özelliklere sahiptir.

| Özellik Adı | Açıklama |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> Anahtar değer çiftlerinde rasgele veri tutan bir. |
| <xref:System.Exception.HelpLink> | Bir url'yi (veya URL'yi) bir özel durum nedeni hakkında kapsamlı bilgiler sağlayan bir yardım dosyasında tutabilir. |
| <xref:System.Exception.InnerException> | Bu özellik, özel durum işleme sırasında bir dizi özel durum oluşturmak ve korumak için kullanılabilir. Daha önce yakalanan özel durumları içeren yeni bir özel durum oluşturmak için kullanabilirsiniz. Özgün özel durum, ek bilgileri incelemek <xref:System.Exception.InnerException> için ikinci özel durumu işleyen kodu niçin izin vererek, özellikteki ikinci özel durum tarafından yakalanabilir. Örneğin, yanlış biçimlendirilmiş bir bağımsız değişken alan bir yönteminiz olduğunu varsayalım.  Kod bağımsız değişkeni okumaya çalışır, ancak bir özel durum atılır. Yöntem özel durum yakalar ve <xref:System.FormatException>bir atar . Arayanın bir özel durum atılma nedenini belirleme yeteneğini geliştirmek için, bazen bir yöntemin yardımcı yordamı tarafından atılan bir özel durumu yakalaması ve ardından oluşan hatanın göstergesi ni daha fazla bir özel durum atması istenir. İç özel durum başvurusu özgün özel durum için ayarlanabileceği yeni ve daha anlamlı bir özel durum oluşturulabilir. Bu daha anlamlı özel durum daha sonra arayana atılabilir. Bu işlevsellikle, önce atılan özel durumla biten bir dizi bağlantılı özel durum oluşturabileceğinizi unutmayın. |
| <xref:System.Exception.Message> | Bir özel durum nedeni hakkında ayrıntılı bilgi sağlar.
| <xref:System.Exception.Source> | Uygulamanın veya hataya neden olan nesnenin adını alır veya ayarlar. |
| <xref:System.Exception.StackTrace>| Bir hatanın nerede oluştuğunu belirlemek için kullanılabilecek bir yığın izleme içerir. Yığın izleme hata ayıklama bilgileri varsa kaynak dosya adı ve program satır numarasını içerir. |

Devralınan sınıfların çoğu <xref:System.Exception> ek üyeler uygulamaz veya ek işlevsellik sağlamaz; onlar sadece <xref:System.Exception>miras . Bu nedenle, bir özel durum için en önemli bilgiler özel durum sınıfları hiyerarşisinde, özel durum adı ve özel durum içerdiği bilgiler bulunabilir.

Yalnızca türetilen nesneleri atmanızı ve yakalamanızı <xref:System.Exception>öneririz, ancak <xref:System.Object> sınıftan türeyen herhangi bir nesneyi özel durum olarak atabilirsiniz. Tüm dillerin türetilen nesneleri fırlatmayı ve <xref:System.Exception>yakalamayı desteklemediğini unutmayın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
