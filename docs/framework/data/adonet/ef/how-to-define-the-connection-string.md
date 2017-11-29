---
title: "Nasıl yapılır: bağlantı dizesi tanımlayın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 757b70d99a7f2b499d4ad5aab2be2bb61b28af0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-the-connection-string"></a>Nasıl yapılır: bağlantı dizesi tanımlayın
Bu konu, kavramsal bir model bağlanırken kullanılan bağlantı dizesi tanımlayın gösterilmektedir. Bu konuda dayanır [AdventureWorks satış](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) kavramsal model. AdventureWorks satış modeli görevle ilgili konulara genelinde kullanılan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belgeleri. Bu konu, zaten yapılandırmış olduğunuz varsayılır, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve AdventureWorks satış modeli tanımlanmış. Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model el ile tanımlamak](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a). Bu konudaki yordamlar da yer alan [nasıl yapılır: bir Entity Framework projesi el ile yapılandırmanız](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Kullanırsanız [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Sihirbazı'nda bir [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] proje, otomatik olarak bir .edmx dosyasının oluşturur ve kullanmak için proje yapılandırır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı kullanın](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>Entity Framework bağlantı dizesi tanımlamak için  
  
-   Projenin uygulama yapılandırma dosyasına (app.config) açın ve bağlantı dizesi olarak şunu ekleyin:  
  
  
  
     Projenizi bir uygulama yapılandırma dosyası yoksa belirleyerek bir tane ekleyebilirsiniz **Yeni Öğe Ekle** gelen **proje** menüsünde seçerek **genel** kategorisi seçme **uygulama yapılandırma dosyası**ve ardından **Ekle**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675)  
 [Nasıl yapılır: yeni bir .edmx dosyasının oluşturma](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)  
 [ADO.NET varlık veri modeli araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
