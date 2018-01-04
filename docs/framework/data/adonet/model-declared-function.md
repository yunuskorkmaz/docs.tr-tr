---
title: "Model bildirilen işlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2f5c7828dc1ea79a548b35109b428da05c2b4560
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="model-declared-function"></a>Model bildirilen işlevi
A *modeli bildirilen işlevi* kavramsal modelde bildirildi, ancak bu kavramsal modelde tanımlı değil bir işlevdir. İşlev barındırma veya depolama ortamında tanımlanabilir. Örneğin, bir model bildirilen işlevi böylece kavramsal modelde sunucu tarafı işlevselliği kullanıma sunan bir veritabanında tanımlı bir işlev eşleştirilmiş olabilir.  
  
 Model bildirilen bir işlevin bildirimi aşağıdaki bilgileri içerir:  
  
-   İşlevin adı. (Gerekli)  
  
-   Döndürülen değerin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    >  Hiçbir değer döndürmeyen belirtilmişse, dönüş türü void alır.  
  
-   Parametre adı ve türü dahil olmak üzere parametre bilgileri. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. CSDL model bildirilen işlevi bir uygulamasıdır bir [işlev içeri aktarması](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d). Aşağıdaki CSDL bir işlev içeri aktarma tanımını içeren bir varlık kapsayıcı tanımlar. Dönüş türü belirtilen beri işlevi için dönüş türü void olduğuna dikkat edin.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
