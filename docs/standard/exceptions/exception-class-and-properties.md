---
title: Özel Durumu Sınıfı ve Özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
ms.openlocfilehash: df05150a5bdd5d24766be252f5cec9a436720d8c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708951"
---
# <a name="exception-class-and-properties"></a>Özel durum sınıfı ve özellikleri

<xref:System.Exception> sınıfı, özel durumların devraldığı temel sınıftır. Örneğin, <xref:System.InvalidCastException> sınıf hiyerarşisi aşağıdaki gibidir:

<xref:System.Object>\
&nbsp;&nbsp;<xref:System.Exception>\
&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.SystemException>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.InvalidCastException>

<xref:System.Exception> sınıfı, bir özel durumun daha kolay anlaşılmasına yardımcı olan aşağıdaki özelliklere sahiptir.

| Özellik Adı | Açıklama |
| ------------- | ----------- |
| <xref:System.Exception.Data> | Anahtar-değer çiftlerinde rastgele verileri tutan bir <xref:System.Collections.IDictionary>. |
| <xref:System.Exception.HelpLink> | Bir özel durumun nedeni hakkında kapsamlı bilgiler sağlayan bir yardım dosyasına bir URL (veya URN) tutabilir. |
| <xref:System.Exception.InnerException> | Bu özellik, özel durum işleme sırasında bir dizi özel durum oluşturmak ve korumak için kullanılabilir. Daha önce yakalanan özel durumları içeren yeni bir özel durum oluşturmak için bunu kullanabilirsiniz. Özgün özel durum, <xref:System.Exception.InnerException> özelliğindeki ikinci özel durum tarafından yakalanarak ek bilgileri incelemek için ikinci özel durumu işleyen koda izin verebilir. Örneğin, yanlış biçimli bir bağımsız değişken alan bir yönteminiz olduğunu varsayalım.  Kod bağımsız değişkenini okumaya çalışır, ancak bir özel durum oluşturulur. Yöntemi özel durumu yakalar ve bir <xref:System.FormatException>oluşturur. Çağıranın bir özel durumun oluşturulma nedenini belirleme yeteneğini geliştirmek için bazen bir yöntem, bir yardımcı yordam tarafından oluşturulan bir özel durumu yakalamak ve sonra gerçekleşen hatanın daha fazla olması için bir özel durum oluşturması istenebilir. İç özel durum başvurusunun orijinal özel duruma ayarlanbildiği yeni ve daha anlamlı bir özel durum oluşturulabilir. Daha sonra bu daha anlamlı bir özel durum çağırana eklenebilir. Bu işlevselliğe, ilk olarak oluşturulan özel durumla biten bir dizi bağlantılı özel durum oluşturduğunu unutmayın. |
| <xref:System.Exception.Message> | Özel durumun nedeni hakkında ayrıntılı bilgi sağlar.
| <xref:System.Exception.Source> | Uygulamanın veya hataya neden olan nesnenin adını alır veya ayarlar. |
| <xref:System.Exception.StackTrace>| Bir hatanın nerede oluştuğunu belirlemede kullanılabilecek bir yığın izlemesi içerir. Yığın izlemesi, hata ayıklama bilgisi varsa kaynak dosya adı ve program satırı numarasını içerir. |

<xref:System.Exception> 'ten kalıtımla alan sınıfların çoğu ek üye uygulamaz veya ek işlevsellik sağlamaz; yalnızca <xref:System.Exception>devralınır. Bu nedenle, bir özel durum için en önemli bilgiler özel durum sınıfları, özel durum adı ve özel durumda bulunan bilgiler hiyerarşisinde bulunabilir.

Yalnızca <xref:System.Exception>türettiğiniz nesneler oluşturmanızı ve yakalanmasını öneririz, ancak <xref:System.Object> sınıfından türetilmiş herhangi bir nesneyi özel durum olarak oluşturabilirsiniz. Tüm dillerin <xref:System.Exception>türetmeyen nesneleri üretilmesini ve bu nesnelerin nasıl desteklemediğini unutmayın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
