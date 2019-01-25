---
title: 'Nasıl yapılır: DBML ve dış eşleme dosyalarını doğrulama'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 42cba5b9b686f5f94d4ebf8f889461e1bab009b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692736"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Nasıl yapılır: DBML ve dış eşleme dosyalarını doğrulama
Dış eşleme dosyalarını ve değişiklik .dbml dosyalarını, karşılık gelen şema tanımlarının karşı doğrulanmalıdır. Bu konu, doğrulama işlemini uygulamak için Visual Studio kullanıcılarıyla adımları sağlar.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>Bir .dbml veya XML dosyasını doğrulamak için  
  
1.  Visual Studio'da **dosya** menüsünde **açık**ve ardından **dosya**.  
  
2.  İçinde **açık dosya** iletişim kutusunda, .dbml ya da doğrulamak istediğiniz XML eşleme dosyası.  
  
     Dosya açılır **XML Düzenleyicisi**.  
  
3.  Pencerenin sağ tıklayın ve ardından **özellikleri**.  
  
4.  İçinde **özellikleri** penceresinde üç nokta simgesine tıklayın **şemaları** özelliği.  
  
     **XML şemaları** iletişim kutusu açılır.  
  
5.  Amacınıza uygun şema tanımı unutmayın.  
  
    -   Bir .dbml dosyası doğrulamak için şema tanımı DbmlSchema.xsd olur. Daha fazla bilgi için [LINQ to SQL'de kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Dış XML eşleme dosyası doğrulamak için şema tanımı LinqToSqlMapping.xsd olur. Daha fazla bilgi için [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  İçinde **kullanım** açılır kutusunu açın ve ardından tıklatıp istediğiniz şema tanımı satırın sütun **Bu şemayı kullan**.  
  
     Şema tanımı, DBML ile ilişkili şimdi veya eşleme dosyası XML dosyasıdır.  
  
     Başka bir şema tanımları seçili olduğundan emin olun.  
  
7.  Üzerinde **görünümü** menüsünü tıklatın **hata listesi**.  
  
     Hataları, uyarıları ve iletileri oluşturulmuş olup olmadığını belirler. Aksi durumda, şema tanımıyla geçerli XML dosyasıdır.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Şema tanımı sağlama için alternatif yöntem  
 Herhangi bir nedenle uygun .xsd içinde dosya görünmüyorsa **XML şemaları** iletişim kutusu, bir Yardım konusunun .xsd dosyasını indirebilirsiniz. Aşağıdaki adımlar indirilen dosyayı Visual Studio XML Düzenleyicisi tarafından gerekli Unicode biçiminde kaydedin yardımcı olur.  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Bir Yardım konusunun bir şema tanımı dosyasını kopyalamak için  
  
1.  Bu konunun önceki kısımlarında açıklandığı gibi şema tanımını içerdiğinden Yardım konusu bulun.  
  
    -   .DBML dosyalar için bkz: [LINQ to SQL'de kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Dış eşleme dosyaları için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Tıklayın **kopyalama kod** kod dosyası panoya kopyalamak için.  
  
3.  Yeni bir dosya oluşturmak için Not Defteri'ni başlatın.  
  
4.  Pano koddan not defteri dosyasına yapıştırın.  
  
5.  Not Defteri'ni üzerinde **dosya** menüsünde tıklayın **Kaydet**.  
  
6.  İçinde **kodlama** kutusunda **Unicode**.  
  
    > [!IMPORTANT]
    >  Bu seçim, 16 Unicode bayt sırası işareti garanti eder (`FFFE`) metin dosyasına eklenir.  
  
7.  İçinde **dosya adı** kutusunda, bir .xsd uzantısı ile adlı bir dosya oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
