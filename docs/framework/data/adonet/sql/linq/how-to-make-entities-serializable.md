---
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: bbe40ec448bef5f62d4182d96f82c6308639e27f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033806"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="664b7-102">Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="664b7-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="664b7-103">Kodunuzu oluşturduğunuzda, varlıkları serileştirilebilir yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="664b7-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="664b7-104">Varlık sınıfları ile düzenlenmiş <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği ve sütunları <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="664b7-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="664b7-105">Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="664b7-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="664b7-106">SQLMetal komut satırı aracı kullanıyorsanız **/serialization** seçeneğini `unidirectional` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="664b7-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="664b7-107">Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="664b7-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="664b7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="664b7-108">Example</span></span>  
 <span data-ttu-id="664b7-109">Aşağıdaki SQLMetal komut satırları, seri hale getirilebilir varlıkların dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="664b7-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="664b7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="664b7-110">See also</span></span>

- [<span data-ttu-id="664b7-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="664b7-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="664b7-112">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="664b7-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
