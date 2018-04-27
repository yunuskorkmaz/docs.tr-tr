---
title: 'Nasıl yapılır: varlıklar seri hale getirilebilir hale getirin'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: b14738e5220810f01b555e54efaad8d8898b7e45
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="09677-102">Nasıl yapılır: varlıklar seri hale getirilebilir hale getirin</span><span class="sxs-lookup"><span data-stu-id="09677-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="09677-103">Kodunuzu oluşturduğunuzda, varlıkları seri hale getirilebilir yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09677-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="09677-104">Sınıflar ile donatılmış <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği ve sütunlarla <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="09677-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="09677-105">Visual Studio kullanarak geliştiricileri kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="09677-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="09677-106">SQLMetal komut satırı aracı kullanıyorsanız **/serialization** seçeneğini `unidirectional` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="09677-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="09677-107">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="09677-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09677-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="09677-108">Example</span></span>  
 <span data-ttu-id="09677-109">Aşağıdaki SQLMetal komut satırlarını seri hale getirilebilir varlık sahip dosyalar üretin.</span><span class="sxs-lookup"><span data-stu-id="09677-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="09677-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09677-110">See Also</span></span>  
 [<span data-ttu-id="09677-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="09677-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [<span data-ttu-id="09677-112">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="09677-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
