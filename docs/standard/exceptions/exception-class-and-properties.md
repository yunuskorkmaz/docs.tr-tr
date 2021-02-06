---
description: 'Daha fazla bilgi edinin: özel durum sınıfı ve özellikleri'
title: Özel Durumu Sınıfı ve Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
ms.openlocfilehash: d45cc50dadf8f48be5cb0017065ea989ae7ae535
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641661"
---
# <a name="exception-class-and-properties"></a>Özel durum sınıfı ve özellikleri

<xref:System.Exception>Sınıfı, özel durumların devraldığı temel sınıftır. Örneğin, <xref:System.InvalidCastException> sınıf hiyerarşisi aşağıdaki gibidir:

<xref:System.Object>\
&nbsp;&nbsp;<xref:System.Exception>\
&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.SystemException>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.InvalidCastException>

<xref:System.Exception>Sınıfı, bir özel durumun daha kolay anlaşılmasına yardımcı olan aşağıdaki özelliklere sahiptir.

| Özellik Adı | Description |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary>Anahtar-değer çiftlerinde rastgele verileri tutan bir. |
| <xref:System.Exception.HelpLink> | Bir özel durumun nedeni hakkında kapsamlı bilgiler sağlayan bir yardım dosyasına bir URL (veya URN) tutabilir. |
| <xref:System.Exception.InnerException> | Bu özellik, özel durum işleme sırasında bir dizi özel durum oluşturmak ve korumak için kullanılabilir. Daha önce yakalanan özel durumları içeren yeni bir özel durum oluşturmak için bunu kullanabilirsiniz. Özgün özel durum, özelliğindeki ikinci özel durum tarafından yakalanarak <xref:System.Exception.InnerException> ek bilgileri incelemek için ikinci özel durumu işleyen koda izin verebilir. Örneğin, yanlış biçimli bir bağımsız değişken alan bir yönteminiz olduğunu varsayalım.  Kod bağımsız değişkenini okumaya çalışır, ancak bir özel durum oluşturulur. Yöntemi özel durumu yakalar ve bir oluşturur <xref:System.FormatException> . Çağıranın bir özel durumun oluşturulma nedenini belirleme yeteneğini geliştirmek için bazen bir yöntem, bir yardımcı yordam tarafından oluşturulan bir özel durumu yakalamak ve sonra gerçekleşen hatanın daha fazla olması için bir özel durum oluşturması istenebilir. İç özel durum başvurusunun orijinal özel duruma ayarlanbildiği yeni ve daha anlamlı bir özel durum oluşturulabilir. Daha sonra bu daha anlamlı bir özel durum çağırana eklenebilir. Bu işlevselliğe, ilk olarak oluşturulan özel durumla biten bir dizi bağlantılı özel durum oluşturduğunu unutmayın. |
| <xref:System.Exception.Message> | Özel durumun nedeni hakkında ayrıntılı bilgi sağlar.
| <xref:System.Exception.Source> | Uygulamanın veya hataya neden olan nesnenin adını alır veya ayarlar. |
| <xref:System.Exception.StackTrace>| Bir hatanın nerede oluştuğunu belirlemede kullanılabilecek bir yığın izlemesi içerir. Yığın izlemesi, hata ayıklama bilgisi varsa kaynak dosya adı ve program satırı numarasını içerir. |

' Den devraldığı sınıfların çoğu <xref:System.Exception> ek üye uygulamaz veya ek işlevsellik sunmaz; bunlar yalnızca ' den devralınır <xref:System.Exception> . Bu nedenle, bir özel durum için en önemli bilgiler özel durum sınıfları, özel durum adı ve özel durumda bulunan bilgiler hiyerarşisinde bulunabilir.

Yalnızca öğesinden türetilen nesneleri oluşturmanızı ve yakalanmasını öneririz <xref:System.Exception> , ancak <xref:System.Object> özel durum olarak sınıftan türeten herhangi bir nesne oluşturabilirsiniz. Tüm dillerin, öğesinden türetilmeyen nesneleri oluşturmamasını ve bu nesnelerin nasıl desteklemediğini unutmayın <xref:System.Exception> .
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
