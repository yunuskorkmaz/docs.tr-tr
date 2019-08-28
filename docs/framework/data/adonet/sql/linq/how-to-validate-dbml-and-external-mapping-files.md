---
title: 'Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041139"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama

Değiştirdiğiniz dış eşleme dosyaları ve. dbml dosyaları kendi şema tanımlarına göre doğrulanması gerekir. Bu konu, Visual Studio kullanıcılarına doğrulama işlemini uygulamak için gereken adımları sağlar.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a>Bir. dbml veya XML dosyasını doğrulamak için

1. Visual Studio **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Dosya**' ya tıklayın.

2. **Dosya Aç** iletişim kutusunda, doğrulamak istediğiniz. dbml veya XML eşleme dosyasına tıklayın.

    Dosya **XML düzenleyicisinde**açılır.

3. Pencereye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

4. **Özellikler** penceresinde, **şemalar** özelliğinin üç nokta simgesine tıklayın.

    **XML şemaları** iletişim kutusu açılır.

5. Amacınıza uygun şema tanımını göz önünde edin.

    - DbmlSchema. xsd, bir. dbml dosyasını doğrulamaya yönelik şema tanımıdır. Daha fazla bilgi için bkz. [LINQ to SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - LinqToSqlMapping. xsd, bir dış XML eşleme dosyasını doğrulamaya yönelik şema tanımıdır. Daha fazla bilgi için bkz. [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

6. İstenen şema tanımı satırının **kullan** sütununda, açılan kutuyu açmak için tıklayın ve ardından **Bu şemayı kullan**' a tıklayın.

    Şema tanımı dosyası artık DBML veya XML eşleme dosyası ile ilişkilendirilmiştir.

    Başka şema tanımlarının seçili olmadığından emin olun.

7. **Görünüm** menüsünde **hata listesi**' a tıklayın.

    Hataların, uyarıların veya mesajların oluşturulup oluşturulmayacağını belirleme. Aksi takdirde, XML dosyası şema tanımına göre geçerlidir.

## <a name="alternate-method-for-supplying-schema-definition"></a>Şema tanımı sağlamak için alternatif Yöntem

Bazı nedenlerle uygun. xsd dosyası **XML şemaları** iletişim kutusunda görünmüyorsa, Yardım konusundan. xsd dosyasını indirebilirsiniz. Aşağıdaki adımlar, indirilen dosyayı Visual Studio XML Düzenleyicisi için gereken Unicode biçiminde kaydetmenize yardımcı olur.

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Yardım konusundan bir şema tanım dosyasını kopyalamak için

1. Şema tanımını içeren yardım konusunu bu konunun önceki kısımlarında açıklandığı gibi bulun.

    - . Dbml dosyaları için bkz. [LINQ to SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - Dış eşleme dosyaları için bkz. [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

2. Kod dosyasını panoya kopyalamak için **kodu kopyala** ' ya tıklayın.

3. Yeni bir dosya oluşturmak için Not defteri 'Ni başlatın.

4. Panodaki kodu Notepad dosyasına yapıştırın.

5. Not defteri **dosyası** menüsünde **farklı kaydet**' e tıklayın.

6. **Kodlama** kutusunda **Unicode**' u seçin.

    > [!IMPORTANT]
    > Bu seçim, Unicode-16 bayt sıra işaretçisinin (`FFFE`) metin dosyasına eklenmiş olmasını sağlar.

7. **Dosya adı** kutusunda. xsd uzantılı bir dosya adı oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
